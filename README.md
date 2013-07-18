send-knockd-one-time-sequences-to-twitter
===================================

Use this script find the last used knockd one time sequence and send it to twitter

Change one_time_sequences to fit your file

The knockd is run as root, so this script su to normal username to send tweets.

This script works with bti for command line twitter client.

Please setup your twitter account with your normal user first.


run from command line with root:

Usage: ./send-knockd-one-time-sequences-to-twitter  your_normal_username


run from knockd by append this script to "start_command" or "command"

example:

[opencloseSMTP]
        one_time_sequences = /etc/knockd.sequences
        seq_timeout        = 15
        start_command      = iptables -A INPUT -s %IP% -p tcp --dport 25 -j ACCEPT; ~username/bin/send-knockd-one-time-sequences-to-twitter  your_normal_username
        cmd_timeout        = 5
        stop_command       = iptables -D INPUT -s %IP% -p tcp --dport 25 -j ACCEPT
