---
sourcePath: ru/_cli-ref/cli-ref/managed-services/managed-clickhouse/shards/update-config.md
---
# yc managed-clickhouse shards update-config

Update the configurationg for a shard.

#### Command Usage

Syntax: 

`yc managed-clickhouse shards update-config <SHARD-NAME> [Flags...] [Global Flags...]`

#### Flags

| Flag | Description |
|----|----|
|`--cluster-id`|<b>`string`</b><br/> ID of the ClickHouse cluster.|
|`--cluster-name`|<b>`string`</b><br/> Name of the ClickHouse cluster.|
|`--async`| Display information about the operation in progress, without waiting for the operation to complete.|
|`--name`|<b>`string`</b><br/> Shard name.|
|`--set`|<b>`key1=value1[,key2=value2][,"key3=val3a,val3b"]`</b><br/> Set parameters for a shard. Can be specified multiple times.|

#### Global Flags

| Flag | Description |
|----|----|
|`--profile`|<b>`string`</b><br/>Set the custom configuration file.|
|`--debug`|Debug logging.|
|`--debug-grpc`|Debug gRPC logging. Very verbose, used for debugging connection problems.|
|`--no-user-output`|Disable printing user intended output to stderr.|
|`--retry`|<b>`int`</b><br/>Enable gRPC retries. By default, retries are enabled with maximum 5 attempts. Pass 0 to disable retries. Pass any negative value for infinite retries. Even infinite retries are capped with 2 minutes timeout.|
|`--cloud-id`|<b>`string`</b><br/>Set the ID of the cloud to use.|
|`--folder-id`|<b>`string`</b><br/>Set the ID of the folder to use.|
|`--folder-name`|<b>`string`</b><br/>Set the name of the folder to use (will be resolved to id).|
|`--token`|<b>`string`</b><br/>Set the OAuth token to use.|
|`--format`|<b>`string`</b><br/>Set the output format: text (default), yaml, json, json-rest.|
|`-h`,`--help`|Display help for the command.|
