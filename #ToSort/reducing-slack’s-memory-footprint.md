# Reducing Slack’s memory footprint

_Captured: 2017-03-03 at 21:28 from [slack.engineering](https://slack.engineering/reducing-slacks-memory-footprint-4480fec7e8eb#.6p1azo7rb)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*vM0VJfoIwi7_gSILWFinuw.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1000/1*vM0VJfoIwi7_gSILWFinuw.jpeg)

> _"Female track athletes at starting line" by tableatny (cc-by)_

_by Johnny Rodgers, Charlie Hess, Raissa Largman, Jamie Scheinblum and Chris Sullivan_

Our desktop app is the most widely used and most capable Slack client that we offer. For many of our customers, it is one of just a few apps they keep open on their computer throughout the work day. It allows them to communicate and work with all the teams they belong to: reading and writing messages, composing posts, uploading files, taking calls, and responding to notifications.

However, these capabilities come at a cost: the desktop client can use a lot of memory. This memory footprint increases as the user signs into more teams, as each team runs in its own webview. More memory usage means worse performance, degrading our customer's experience of Slack and their other applications.

Work is underway to fix the underlying factors affecting client memory consumption, but in the meantime **we've built a tiny new Slack client to help address this issue**. It is loaded silently in place of the teams that you haven't looked at in a while. This background client does just a few things:

  * updates your unread indicator and notification badge in the team sidebar
  * displays desktop notifications _(that you can click on and reply to as normal)_
  * consumes as little memory as possible

To achieve this we had to teach our servers to be smarter, and to design a thin client that did just enough work to keep your work day flowing.

#### The problem

At the time of writing, about 36% of active Slack users are signed into more than one team in the desktop app. 17% are signed into 3 or more teams, and 5% are signed into 5 or more teams. Each of these teams is running the full JavaScript web application and maintaining and updating the DOM tree as the state of the team changes. This application can consume between ~130MB (p10) and ~960MB (p99) of memory depending on team activity and UI state.

> _Distribution of memory usage at p10, p50, p90, and p99 for a single team. Collected using a 10% sample of all teams._

Our data tells us that most people who are signed into multiple teams have 1 or 2 that they actively pay attention to during their work day while they check the others less frequently. Regardless of usage, each of these teams eats up a full quota of memory.

#### **A tiny client**

This got us thinking: what is the lightest weight client we could build that could do everything you needed it to do while it was in the background: maintain your presence, display notifications, and keep your unreads and badges up to date?

We explored several options, including:

  1. unload the DOM for backgrounded teams
  2. package a client out of a subset of our JavaScript concerned with just model and notification logic
  3. build a stripped-down client specifically for this purpose

Our exploration indicated that the first two options either didn't make the impact on memory usage that we were targeting, or increased the complexity of implementation for our primary client unacceptably. So we decided on the third option and built a thin client that maintains minimal state and only presents data as transmitted by the server.

The aspect of the project concerned with reclaiming resources from backgrounded views isn't original. Chrome takes a similar approach to [tab discarding](https://developers.google.com/web/updates/2015/09/tab-discarding) in order to recover memory from backgrounded tabs, and several popular browser extensions similarly [suspend](https://chrome.google.com/webstore/detail/the-great-suspender/klbibkeccnjlkjkiokjodocebajanakg) [memory-hungry tabs](https://addons.mozilla.org/en-US/firefox/addon/suspend-tab/) that haven't been viewed recently.

#### Redrawing the map

In order for our new client to be as thin and lightweight as we needed it to be, we had to teach the server to do a lot of work that was previously the responsibility of the client.

For example, the server now needs to know:

  * How to calculate a user's notification count
  * Which messages qualify for desktop notifications _(and how to format those notifications for consumption by the desktop client)_
  * Whether the user had any unreads across all of their channels and direct messages

And it needs to do all this with full awareness of the impact of various team and user preferences and states on the above. Slack is known for its granular and powerful notification preferences -- which is great for customers but meant we needed to migrate a good deal of client-side logic to the server:

> _Workflow diagram encompassing all the considerations that go into whether to notify a user about a message._

We developed two pieces of infrastructure to achieve these new requirements.

  1. An API endpoint that returns whether a user **has_unreads** and their **mention_count**. It stores this data in memcache for rapid retrieval. The tiny client polls this endpoint to keep the team sidebar up to date for backgrounded teams.
  2. New logic in the server-side message processing code to convert notification-causing messages into a new **desktop_notification** message type, which is then distributed over the websocket. Currently, only the tiny client pays attention to this type of message. The client uses the payload of this message to pop a desktop notification if the user has notifications enabled.

> _The team sidebar in the desktop app displays an unread indicator and a notification badge._

The tiny client can utilize these tools to do precisely the things it needs to while running in the background: keep your team sidebar up to date with your unread and badge count, and display notifications as the full client does. The client itself is a single JavaScript file of about 1200 lines of unminified code. It keeps _just enough_ model and state data in order to achieve its purposes, and is replaced with the full web application when the team is foregrounded.

Swapping between clients is managed by the desktop application, which monitors team usage and time elapsed since a team was last checked. We measure both which teams you use most often, and those you've checked recently, and after a period of inactivity unload those teams that are less likely to be foregrounded.

#### Results

The minimal client dramatically reduces the memory required to run a team in the Slack desktop application, as shown below. This helps to reduce the overall footprint of the app and release resources back to the operating system to improve performance for the teams you are actively using.

> _Comparison of memory usage at p10, p50, p90, and p99 for a single team running the full client (left) and minimal client (right). Collected using a 10% sample of all teams._

#### **What's next?**

We are actively working on a number of projects to reduce the memory footprint of the full client. These in-flight efforts include:

  * **Refactoring the JavaScript codebase** to more clearly separate concerns and make each layer more efficient.
  * **Migrating to an incomplete model **of all team data (fetched on demand rather than up front). This is already the case for users and bots.
  * **Switching to subscription models** for high volume events (for example: user presence changes).
  * **Adopting reactive UI components** to reduce churn in the DOM. This is already the case for the Emoji Picker.
  * Exploring running **all teams in a shared context** to eliminate the overhead of one webview per team.

In the meantime, we hope our tiny new client will ease the burden on our customer's computers and improve their experience of Slack.
