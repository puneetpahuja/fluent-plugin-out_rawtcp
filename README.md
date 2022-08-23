# Raw MsgPack for Fluentd

Used to chain `fluentd -> logstash`

Fluentd's `out_forward` plugin uses a custom serialization mechanism that prevents interaction with logstash (input tcp + msgpack codec).  
This plugin implements a simple TCP forward, without heartbeats or any other out-of-band checks.

## Installation

`$ gem install fluent-plugin-out_rawtcp-godel`

## Usage
```xml
<match **>
  type rawtcp
  buffer_type file
  buffer_path /var/log/fluent/logcentral
  <server>
    name log1
    host 10.0.1.165
    port 24224
  </server>
</match>
```
Multiple `<server>` entries can be configured and logs will be sent to the first active one.


## Acknowledgement

Inspired by fluentd's out_forward plugin by FURUHASHI Sadayuki
