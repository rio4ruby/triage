# README

Usage: triage -h hosts -c command [-c command]

Requires

    gem install net-ssh
    gem install rio

Run multiple commands on multiple hosts simultaneosly.
Hosts must be defined in your .ssh/config file as in

```
  Host server1
       HostName rails1.com
       Port 22
       User fred
  Host server2
       HostName rails2.com
       Port 7822
       User betty
```

Use case:

Typically in a production environment several servers are running,
any one of which may handle a particular request. triage allows
one to perform the same action on all simultaneously, rather than
opening seperate windows for each.

With multiple rails servers, one can follow the logs of all simultaneously

    ./triage -h server1,server2 -c 'tail -f /railsapp/log/production.log'

Or search all simultaneously

    ./triage -h server1,server2 -c 'grep whatIamLookingFor /railsapp/log/production.log'

