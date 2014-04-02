logfilters
==========

This repo contains a simple YAML file containing useful Eucalypus log messages for use with filters in log-watching and monitoring systems.  If you're using Logstash, Graylog or Splunk-like like mechanism to analyse logs then these filters are a useful starting point for picking up activities in the cloud (such as an instance launch, or a node failure).

The file follows a YAML syntax but you could always run this through something else if you want (maybe even convert via http://yaml-online-parser.appspot.com) via pyaml or such.

Each item has a number of keys, for example:

    - line: libvirt_err_handler
      description: a libvirt-related error has occured on a node
      log: nc.log
      type: error
      component: nc
    
explained as:
      
key | value
---- | -----
line |   this is the string to match in the Eucalyptus log file
description |  this is a brief description of the error or event
log |  this is the file in which this message could be found
type |  indicates whether its an error condition or an event.  An error would be something which requires the administrator to act to avoid a problem(tm).  An event is an indication of normal cloud usage (like a user launching an instance).
component | this is the component on which this log and message can be found.  This grouping would potentially allow you to automate distribution of filters based on information in this file. 
