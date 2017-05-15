# pm2-telegram-notify

This is a PM2 Module is started as fork from mattpker/pm2-slack

## Install

To install and setup pm2-telegram-notify, run the following commands:

```
pm2 install pm2-telegram-notify
```


## Configure

The following events can be subscribed to:

- log - All standard out logs from your processes. Default: false
- error - All error logs from your processes. Default: true
- kill - Event fired when PM2 is killed. Default: true
- exception - Any exceptions from your processes. Default: true
- restart - Event fired when a process is restarted. Default: false
- reload - Event fired when a cluster is reloaded. Default: false
- delete - Event fired when a process is removed from PM2. Default: false
- stop - Event fired when a process is stopped. Default: false
- restart overlimit - Event fired when a process is reaches the max amount of times it can restart. Default: true
- exit - Event fired when a process is exited. Default: false
- start -  Event fired when a process is started. Default: false
- online - Event fired when a process is online. Default: false

You can simply turn these on and off by setting them to true or false using the PM2 set command.

```
pm2 set pm2-telegram-notify:log true
pm2 set pm2-telegram-notify:error false
```

## Options

The following options are available:

- username (string) - Set the username used in Slack for posting the message. By default this is the hostname of the server.
- buffer (bool) - Enable/Disable buffering of messages by timestamp. Messages that occur with the same timestamp (seconds) will be concatenated together and posted as a single slack message. Default: true
- buffer_seconds (int) - Duration in seconds to aggregate messages. Has no effect if buffer is set to false.  Min: 1, Max: 5, Default: 1
- queue_max (int) - Number of messages to keep queued before the queue will be truncated. When the queue exceeds this maximum, a rate limit message will be posted to slack. Min: 10, Max: 100, Default: 100

Set these options in the same way you subscribe to events.

Example: The following configuration options will enable message buffering, and set the buffer duration to 2 seconds.  All messages that occur within 2 seconds of each other (for the same event) will be concatenated into a single slack message.

```
pm2 set pm2-telegram-notify:username pm2-user
pm2 set pm2-telegram-notify:buffer true
pm2 set pm2-telegram-notify:buffer_seconds 2
```

## Contributing

In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code.

## Release History

- 0.1.0 Initial Release