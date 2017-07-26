# Ulysses X-Callback-URL Support

_Captured: 2016-03-13 at 19:10 from [ulyssesapp.com](http://ulyssesapp.com/kb/x-callback-url/)_

Ulysses supports [x-callback-urls](http://x-callback-url.com/), allowing other apps to trigger certain actions in Ulysses such as creating new sheets.

## The URL Scheme

The used scheme is `ulysses://`. Every action can be called through the x-callback-url API using the following format:
    
    
    ulysses://x-callback-url/[action]?[x-callback parameters]&[parameters]
    

For more information regarding the URL format, see the [official specification](http://x-callback-url.com/specifications/).

## Available Actions

In the following, all available actions are detailed. Please note that for reasons of clarity, the examples are not yet URL escaped. For instance, all whitespace must be replaced with `%20`.

### `new-sheet`

Creates a new sheet.

**Parameters:**

  * `group`  
The name of the group the sheet should be inserted to. If this parameter is missing, the sheet is created in the Inbox folder. If a pure name is given (e.g. `My Group`), the sheet is created in the first group matching regardless whether the group is on top level or nested. Alternatively a path can be specified, to address a specific, nested group. A path must begin with a slash (e.g. `/My Group/My Subgroup`).
  * `text`  
The contents that should be inserted to the new sheet. Must be URL-encoded Markdown.

**Example:** `[ulysses://x-callback-url/new-sheet?text=My new sheet`](ulysses://x-callback-url/new-sheet?text=My%20new%20sheet)

### `new-group`

Creates a new group.

**Parameters:**

  * `name`  
The name of the group to be created.
  * `parent`  
The name of the parent group the new group should be inserted to. If this parameter is missing, the sheet is created in the Inbox folder. If a pure name is given (e.g. `My Group`), the sheet is created in the first group matching regardless whether the group is on top level or nested. Alternatively a path can be specified, to address a specific, nested group. A path must begin with a slash (e.g. `/My Group/My Subgroup`).

**Example:** `[ulysses://x-callback-url/new-group?name=My Group`](ulysses://x-callback-url/new-group?name=My%20Group)

### `open-group`

Open a group with a particular name in Ulysses.

**Parameters:**

  * `name`  
The name of the group that should be opened. If a pure name is given (e.g. `My Group`), the sheet is created in the first group matching regardless whether the group is on top level or nested. Alternatively a path can be specified, to address a specific, nested group. A path must begin with a slash (e.g. `/My Group/My Subgroup`).

**Example:** `[ulysses://x-callback-url/open-group?group=My Group`](ulysses://x-callback-url/open-group?group=My%20Group)

### `open-all`, `open-recent`, `open-favorites`

Opens the special groups "All", "Last 7 Days" and "Favorites".

## x-callback Parameters

In addition to action parameters, generic x-callback parameters can also be included. All of these are optional.

  * `x-source`  
The name of the source app calling the action.
  * `x-success`  
URL to open to return to the source app. If not provided, the user stays in Ulysses.
  * `x-error`  
URL to open if the requested action generates an error in Ulysses. Currently, this is only the case for open-stack. If a stack cannot be found, an error description and error code "1" is returned.
  * `x-cancel`  
URL to open if the requested action is cancelled by the user. Currently not used by Ulysses.

Example: If a new sheet should be created and the user wants to return to the calling app (say, "SourceApp") afterwards, use the following URL (line breaks are for legibility):
    
    
    ulysses://x-callback-url/new-sheet?
        x-source=SourceApp&
        x-success=sourceapp://x-callback-url/success&
        group=Lecture Notes
    
