# Sean's Technical Ramblings

_Captured: 2017-11-08 at 11:21 from [seanb.co.uk](https://seanb.co.uk/2017/11/camera-snapshots-updated/)_

A really quick one today to update my post about [camera snapshot notifications](https://seanb.co.uk/2017/10/camera-snapshot-notifications-in-home-assistant/) in Home Assistant.

In that post I showed the shell command you could use to take a snapshot from any camera visible to Home Assistant. In the very next release, that functionality was added to the [camera component](https://home-assistant.io/components/camera/) so that you can call a service directly from within Home Assistant.

Instead of using a shell command:

`action:``\- service: shell_command.take_snapshot``data_template:``url: 'http://localhost:8123{{ states.camera.mjpeg_camera.attributes.entity_picture }}'``filename: '/tmp/snapshot.jpg'`

You can now simply write:

`action:``\- service: camera.snapshot``data:``entity_id: camera.mjpeg_camera``filename: "/tmp/snapshot.jpg"`

And of course you no longer need the shell command defined.

There is one other thing you need to do to configure it. You need to add the path to the whitelist of directories to which Home Assistant can write. This goes into your configuration.yaml under the homeassistant section:

`whitelist_external_dirs:``\- /tmp`

I think this is a great change - it just feels cleaner to do it all directly within Home Assistant.

As it's now a service, it's also easy to test from the front end using the service call under developer tools:

![](https://seanb.co.uk/wp-content/uploads/2017/11/ha-snapshot-service.png)

There is another [change](https://github.com/home-assistant/home-assistant/pull/9967) in 0.57 that turned out to be a breaking change for my method of showing the snapshot and then hiding it when the notification is dismissed.

Instead of the state of a persistent notification being the full notification text, it is now set to "notifying" and the message and title are available as attributes. That means that instead of the notification dismissal trigger from my example being:

`trigger:``platform: state``entity_id: persistent_notification.doorbell``from: "Doorbell rung"`

It should be:

`trigger:``platform: state``entity_id: persistent_notification.doorbell``from: "notifying"`

I like this change as well. I wasn't really happy with hard coding the text of the notification in the trigger as it forced you to change the trigger if you changed the text of the notification to keep it in sync with the notification. Again, I think the new way is much cleaner and satisfies the [DRY principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself).

I've edited the original blog post to reflect this change but I thought it was worth another quick post about the changes. They're both changes for the better and highlight how quickly Home Assistant is evolving.

It's always worth keeping an eye on the changelog for updates - not only are new platforms added with every release, the core functionality of the existing components keeps growing as well.

in [Home Automation](https://seanb.co.uk/category/home-automation/)
