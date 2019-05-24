# Slack Notifications Skillet

This skillet configures HTTP notifications to a Slack webhook for monitoring of events on a PAN-OS firewall.  This posts important 
system, threat, and traffic log entries to a channel of your choice, making monitoring of a home firewall (or any low traffic firewall) easy.  This is also intended to demonstrate how to integrate PAN-OS with a typical HTTP webhook. 

## Setting up the Slack webook

_To be added_

## Usage

### Parameters

- **webhook_uri_format**: This is the portion of the generated webhook URL without `https://hooks.slack.com/`.
- **profile_name**: Name of the HTTP server profile that gets created.
- **fw_name**: String prefix that gets added to messages posted to the Slack channel.  This is useful if you have multiple 
  firewalls sending events to a single channel.

### Outputs

Running this skillet will configure:

- An HTTP server profile for the Slack webhook‘s URL
- Critical and high system logs to the Slack webhook
- Logging profile to forward critical and high threat and Wildfire events to the webhook
- Logging profile to forward traffic events to the webhook

### Intended Usage

Critical and high system logs are forwarded to the channel using the *Slack System Logs* profile.

_Screenshot of profile_

Critical and high threat and Wildfire events are forwarded to the channel using the *Slack Default* profile.  This is intended to be the default logging profile for rules, only forwarding events that need immediate admin follow up.

_Screenshot of profile and example rule_

All traffic matches are forwarded to the channel by the *Slack Outbound Alert*.  This is intended to notify the admin of traffic to known compromised hosts, or any traffic you want to know about immediately.

_Screenshot of profile and example rule_
