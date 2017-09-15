# The Longest Email I Ever Sent (Programmatically)

_Captured: 2017-08-19 at 18:20 from [dzone.com](https://dzone.com/articles/the-longest-email-i-ever-sent-programmatically?edition=317400&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-18)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

It was a quiet day in July when I got a message from SendGrid about a service I run, [CodeTriage, which helps people contribute to open source projects](https://www.codetriage.com/), had gone over its limits. Calls to send out emails were all failing. The fix was easy: bump up the limits by going to the Heroku dashboard, click "edit," and adjust the plan. Previously I got notifications that I was almost out of credits for the service, but since it was SOOO close to the end of the month, I thought I could squeak by without having to upgrade. I was wrong. No biggie though, as soon as I upgraded my add-on emails started to flow again. It wasn't until later that I got the bug report, while I was successfully sending out emails, they were MASSIVE. Some of the people who got them couldn't even open the emails, they were causing the clients to crash. Before we can understand why we need to understand how the service sends out emails.

The service works by sending people links to open OSS issues in their inbox, or for Ruby apps links to methods that can be documented. It is an "email first" interface, and if emails aren't working then the whole app is effectively down. The idea behind sending users open issues is that they can help "triage" them. Ask the reporter for specific version numbers, or for an app that reproduces the behavior. As such, when a core contributor to the project gets to that issue, there is less that needs to be done, the issue no longer needs triage and is ready to be worked on.

What usually happens is I have a task that runs via the [Heroku Scheduler](https://elements.heroku.com/addons/scheduler) every hour. Users specify what time of day they want emails and when it's their hour we send them an email. We also have some "backoff" logic so that people who aren't terribly active don't get overwhelmed. We start sending emails daily, then weekly, then every other week etc. You can also configure the "minimum" frequency of emails you want to get. Not everyone can power through a half dozen issues every week, I understand.

The high-level logic looks like this:
    
    
        return false if user.repo_subscriptions.empty?
    
    
        return false if email_sent_in_last_24_hours?(user)

If you pass all those criteria we send you an email.

But before we can send you issues, we have to have a list of issues. To generate that we look at the OSS repositories you're subscribed to. Then we have to see what issues are open, which you've already been sent, and for a final check make sure that you've not commented on the issue already.

You can see here where we build the issue list before we send out the email:
    
    
      mail = UserMailer.send_daily_triage(user_id: user.id, assignment_ids: assignments.pluck(:id)).deliver
    
    
      user.repo_subscriptions.update_all(last_sent_at: Time.now)

Once emails successfully go out, we update the "assignments" to mark them as "delivered" and record the last time that we sent you an email.

So far so good.

Normally, users who subscribe to a few repos will get a handful of issues per email with 6-12 being pretty reasonable. When I opened up a bug report on the issue tracker I had a user reporting a whopping [473 issues](https://github.com/codetriage/codetriage/issues/600) in the email. The email was so large that their client couldn't even render the email. Yikes.

This is to date, the largest programmatically generated email I've ever sent (not including attachments).

When I got the issue report I went through the stages of programmer bug grief, starting with "that's not possible." I skimmed all my code, without finding where the issue could have been, so I decided to manually walk through generating an email to send to see if I could reproduce the issue.

Here's the code to see the assign issues:
    
    
      issue_assignments.where(delivered: false).limit(daily_issue_limit)

I went into a console session to reproduce the behavior:
    
    
    user = User.where(github: 'schneems').first

> Note: I'll use my GitHub username for the examples.

Strange: it looked fine. No abnormally high issue counts. When I went through this exercise I realized that I already had a feature `daily_issue_limit` that could be used to set a max number of issues to get per email.

It's important not only to fix bugs but to also fix experiences. In this case, I didn't want any users to quit because they're spammed with really large emails. So even though I didn't know how to fix the bug or even what the bug was, I knew that if I could limit the number of issues they got, then the experience would be "fixed." I could then buy myself time to dig into the issue.

I apologized for the issue and suggested they set that value to a low number. I then decided that there should be a default for that value. I pulled a magic number of 50 out of the air and [set that as a new default on the column](https://github.com/codetriage/codetriage/pull/601).

> Note: I manually updated all existing user's values in a console session.

When you can't fix a bug, and especially when you can't isolate it, it's important to treat the symptoms as well. If you've worked in support this is known as a "workaround," and while it should always be temporary (you need a long-term solution), it should be at the top of your mind when interacting with customers (users).

It wasn't until completely by coincidence someone opened a [PR to make all emails "deliver_later."](https://github.com/codetriage/codetriage/pull/602) In the conversation on the PR, it was pointed out that even if emails are already sent out in background workers, it's still good practice to `deliver_later` because there might be an issue in sending the emails (like we ran out of SendGrid credits). Sidekiq (our background job library) will auto retry failed jobs. If an email send needs to be retried, it's best to not also have to retry all the logic associated with it.

Do you catch the problem yet?

The key unspoken word here is "idempotent." Each job needs to be side effect free so it can safely be retried. But it's currently not. Each time we tried to send emails it would fail and put the job back into the Sidekiq queue to be retried. We also tried to send emails every hour. Every time the job ran, new issues were being assigned even though they weren't being delivered:
    
    
    issue_assignments.where(delivered: false).limit(daily_issue_limit)

This code got called over and over again. Each time that list of issue assignments that were not delivered grew and grew, until finally: I fixed the SendGrid issue. The next email to go out had ALL the previously assigned issues, not just the most recent. Yikes.

I merged in the `deliver_later` PR to help mitigate issues like this from happening in the future.

I still haven't gone back to make that task idempotent. To do that I could check to see if any non-delivered issues existed and skip the `assign!` step. Alternatively, I could unassign any non-delivered assignments before re-running the assigner. Either of these changes would make the task far more robust.

I have a confession to make. This post isn't really about sending emails. It's about messing up expectations of your system and your users.

I failed by not fully understanding the idempotent requirement of my background jobs. I knew that background jobs can be retried. I knew "SendGrid was down." I knew that "SendGrid came back up." I knew that "a user got a huge email" but I still didn't connect the failure dots.

I messed up when I didn't have any "sensible" default for my `daily_issue_limit`. While 50 was plucked from thin air, any "reasonable" number should have been good enough. When adding any new user settable options, consider what the "worst" case would be if it wasn't set. Consider adding a default with that in mind.

I also wasn't following the best practices of always delivering emails in their own background job. Heck, I hadn't even considered why exactly that would be needed if emails were being sent from within another background job already.

We will all mess up at some point or another. When we do it's also important to accept your responsibility to your customers. Get them up and running while minimizing the impact or asking them to jump through too many hoops. Keep your head above the water, and keep your emails normal sized.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
