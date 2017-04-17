# Local notifications on macOS for remote irssi events.

This script has a very simple purpose: it monitors a remote irssi session (as in the case when running irssi in tmux or screen on a remote machine) and pops up [growl](http://growl.info) notifications on your local machine when you have new mentions, direct messages, or optionally when activity occurs in a list of named channels.


This script and general approach was adopted from [this blogpost](http://mlomnicki.com/ruby/linux/2011/02/09/irc-notifications.html) by [Michał Łomnicki](https://github.com/mlomnicki).

## Installation

 - install growl, and the `growlnotify` command line tool from the [growl website](http://growl.info/downloads). 
 - clone this reposity or copy `mac_irssi_notify.py` to the location of your choice. Run `chmod+x mac_irssi_notify.py` to make the script executable. 
 - set up the `autolog` feature in irssi. There is some info [here](https://irssi.org/documentation/settings/). 
 - make sure your logs are using the default irssi theme, with `\set log_theme default`.

## Usage

`ssh user@server "tail -n0 -f ~/irclogs/*/*.log" | mac_irssi_notify.py -u username -c #some #channels`.

The first part remotely executes the `tail` command, which prints new lines as they are written to the logs. If you've set your logging directory to be other than the default, put it in the place of `~/irclogs`. The part after the `|` is the script. The arguments are simple: -u lets you specify a word to monitor (e.g. your username) and `-c` lets you specify any number of channels; you will receive notifications for all events in these.


## Contributions

If this is useful to you it probably needs to be improved. Open an issue and let's chat about it. :)
 

