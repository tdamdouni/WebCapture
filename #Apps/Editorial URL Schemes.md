# Editorial URL Schemes

_Captured: 2016-03-03 at 17:49 from [omz-software.com](http://omz-software.com/editorial/docs/ios/urlscheme.html)_

You can launch Editorial from other apps using the editorial:// URL scheme. Apart from just launching the app, you can open an existing file in your library, create a new file with a given name, and run workflows.

The general pattern of an Editorial URL is this:

editorial://<action>/<filename>?root=<dropbox|local>&selection=<from-to>&command=<command name>&input=<command input>

  * action can be open or new

  * filename is either the name of the file to open (if action is open), or the name of the new file to create (if action is new). If a file with the given name already exists, a numeric suffix is automatically appended.

  * root can be dropbox or local. If omitted, local is assumed.

  * command optionally specifies an editor command (workflow) by name that should be executed after opening or creating the file. If there are multiple workflows with the same name, the first one is executed. You can also leave out the action and filename parameters to execute a command without opening or creating a file, for example:

> editorial://?command=My%20Command.

  * input optionally specifies the input for the first action in the workflow that is run with the command parameter.

  * selection is an optional parameter for setting the initial selected text range when opening or creating a file. It is specified as from-to, for example 0-10 to select the first 10 characters. The to part can be omitted if you don't want to select any text, but scroll to a specific position. If you want to scroll to the end of the text, you can just use a very large number for from. Selections that go beyond the length of the text will automatically be capped.

In addition to the app-specific parameters above, Editorial also supports the x-callback-url standard. x-callback parameters only have an effect when the command parameter is used to run a workflow.

  * x-success Specifies a URL to open when the workflow finishes without errors. If the URL contains the placeholder [[output]], it is replaced with the (URL-escaped) output of the last action in the workflow.
  * x-cancel This URL is opened when a workflow is cancelled. No additional parameters are appended to this URL.
  * x-error If this parameter is used and the workflow generates an error, the error message is not shown. Instead, the given URL is opened with an errorMessage and errorCode parameter appended. errorCode will usually just be -1, it is just included to ensure compatibility with other apps that may rely on a value being there.

Note

If Editorial is not already running when a URL is opened, the normal behavior of restoring the previous document is skipped. This can be useful if you encounter problems launching the app. An exception is the URL editorial://back - you can use this if you just want to open Editorial, without doing anything else.

## Version-specific URL Schemes

Starting with Editorial 1.1, there are additional URL schemes for detecting the installed version from other apps. For example, with version 1.1, the additional schemes editorial-v100://, editorial-v110:// and editorial-v120:// are supported. A different app could check for these schemes to detect if a specific update is installed, in case it depends on features that weren't available in older versions.

The behavior of the version-specific schemes is equivalent to the default (editorial://) scheme.
