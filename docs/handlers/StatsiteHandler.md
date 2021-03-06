StatsiteHandler
====

Send metrics to a [Statsite](https://github.com/armon/statsite/)
using the default interface.

Statsite
========

This is a stats aggregation server. Statsite is based heavily
on Etsy's [StatsD](https://github.com/etsy/statsd). This is
a re-implementation of the Python version of
[statsite](https://github.com/kiip/statsite).

Features
--------

* Basic key/value metrics
* Send timer data, statsite will calculate:
  - Mean
  - Min/Max
  - Standard deviation
  - Median, Percentile 95, Percentile 99
* Send counters that statsite will aggregate


Architecture
-------------

Statsite is designed to be both highly performant,
and very flexible. To achieve this, it implements the stats
collection and aggregation in pure C, using libev to be
extremely fast. This allows it to handle hundreds of connections,
and millions of metrics. After each flush interval expires,
statsite performs a fork/exec to start a new stream handler
invoking a specified application. Statsite then streams the
aggregated metrics over stdin to the application, which is
free to handle the metrics as it sees fit.

This allows statsite to aggregate metrics and then ship metrics
to any number of sinks (Graphite, SQL databases, etc). There
is an included Python script that ships metrics to graphite.

Additionally, statsite tries to minimize memory usage by not
storing all the metrics that are received. Counter values are
aggregated as they are received, and timer values are stored
and aggregated using the Cormode-Muthurkrishnan algorithm from
"Effective Computation of Biased Quantiles over Data Streams".
This means that the percentile values are not perfectly accurate,
and are subject to a specifiable error epsilon. This allows us to
store only a fraction of the samples.

#### Options - [Generic Options](Configuration)

<table><tr><th>Setting</th><th>Default</th><th>Description</th><th>Type</th></tr>
<tr><td>get_default_config_help</td><td></td><td>get_default_config_help</td><td></td></tr>
<tr><td>host</td><td></td><td></td><td>str</td></tr>
<tr><td>server_error_interval</td><td>120</td><td>How frequently to send repeated server errors</td><td>int</td></tr>
<tr><td>tcpport</td><td>1234</td><td></td><td>int</td></tr>
<tr><td>timeout</td><td>5</td><td></td><td>int</td></tr>
<tr><td>udpport</td><td>1234</td><td></td><td>int</td></tr>
</table>

### This file was generated from the python source
### Please edit the source to make changes

