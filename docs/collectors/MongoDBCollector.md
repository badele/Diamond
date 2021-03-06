MongoDBCollector
=====

Collects all number values from the db.serverStatus() command, other
values are ignored.

**Note:** this collector expects pymongo 2.4 and onward. See the pymongo
changelog for more details:
http://api.mongodb.org/python/current/changelog.html#changes-in-version-2-4

#### Dependencies

 * pymongo

#### Example Configuration

MongoDBCollector.conf

```
    enabled = True
    hosts = localhost:27017, alias1@localhost:27018, etc
```

#### Options - [Generic Options](Configuration)

<table><tr><th>Setting</th><th>Default</th><th>Description</th><th>Type</th></tr>
<tr><td>byte_unit</td><td>byte</td><td>Default numeric output(s)</td><td>str</td></tr>
<tr><td>collection_sample_rate</td><td>1</td><td>Only send stats for a consistent subset of collections. This is applied after collections are ignored via ignore_collections Sampling uses crc32 so it is consistent across replicas. Value between 0 and 1. Default is 1</td><td>int</td></tr>
<tr><td>databases</td><td>.*</td><td>A regex of which databases to gather metrics for. Defaults to all databases.</td><td>str</td></tr>
<tr><td>enabled</td><td>False</td><td>Enable collecting these metrics</td><td>bool</td></tr>
<tr><td>host</td><td></td><td>A single hostname(:port) to get metrics from (can be used instead of hosts and overrides it)</td><td></td></tr>
<tr><td>hosts</td><td>localhost,</td><td>Array of hostname(:port) elements to get metrics fromSet an alias by prefixing host:port with alias@</td><td>list</td></tr>
<tr><td>ignore_collections</td><td>^tmp\.mr\.</td><td>A regex of which collections to ignore. MapReduce temporary collections (tmp.mr.*) are ignored by default.</td><td>str</td></tr>
<tr><td>measure_collector_time</td><td>False</td><td>Collect the collector run time in ms</td><td>bool</td></tr>
<tr><td>metrics_blacklist</td><td>None</td><td>Regex to match metrics to block. Mutually exclusive with metrics_whitelist</td><td>NoneType</td></tr>
<tr><td>metrics_whitelist</td><td>None</td><td>Regex to match metrics to transmit. Mutually exclusive with metrics_blacklist</td><td>NoneType</td></tr>
<tr><td>network_timeout</td><td>None</td><td>Timeout for mongodb connection (in milliseconds). There is no timeout by default.</td><td>NoneType</td></tr>
<tr><td>passwd</td><td>None</td><td>Password for authenticated login (optional)</td><td>NoneType</td></tr>
<tr><td>replica</td><td>False</td><td>True to enable replica set logging. Reports health of individual nodes as well as basic aggregate stats. Default is False</td><td>bool</td></tr>
<tr><td>simple</td><td>False</td><td>Only collect the same metrics as mongostat.</td><td>str</td></tr>
<tr><td>ssl</td><td>False</td><td>True to enable SSL connections to the MongoDB server. Default is False</td><td>bool</td></tr>
<tr><td>translate_collections</td><td>False</td><td>Translate dot (.) to underscores (_) in collection names.</td><td>str</td></tr>
<tr><td>user</td><td>None</td><td>Username for authenticated login (optional)</td><td>NoneType</td></tr>
</table>

#### Example Output

```
__EXAMPLESHERE__
```

### This file was generated from the python source
### Please edit the source to make changes

