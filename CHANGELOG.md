# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

You can find a list of previous releases on the [github releases](https://github.com/uber/cadence/releases) page.

## [1.2.1] - 2023-08-24
### Added
Added guardrail to on scalable tasklist number of write partitions (#5331)
Added Opensearch2 client with bulk API shared between clients (#5241)
Added Filters method to dynamic config Key (#5346)
Added domain migration validator command (#5369, #5374)
Added docker-compose with http API enabled (#5358)
Added support to enable TLS for HTTP inbounds (#5381)

### Fixed

### Changed
Updates to partition config middleware (#5334)
Allow to configure HTTP settings using template (#5329)
Cleanup the unused watchdog code (#5096)
Upgrade yarpc to v1.70.3 (#5341)
upgrade mysql (#5345)
change mysql schema folder v57 to v8 (#5356)
Remove duplicated line (#5328)
Fill IsCron for proto of WorkflowExecutionInfo (#5366)
Update idls and ensure thrift fields roundtrip (#5365)
Go version bump (#5367)
Update Dockerfile with a proper Go version and bump alpine version (#5371)
StartWorkflowExecution: validate RequestID before calling history (#5359)
Update list of available frontend HTTP endpoints (#5338)
Set a minimum timeout for async task dispatch based on rate limit (#5382)
Validate search-attribute-key so keys are fine in advanced search (#5340)

## [1.2.0] - 2023-08-24
### Added
Added more logs around unsupported version for consistent query (#5287)
Added datasource and dashboards to Grafana in Docker (#5207)
Added metric for isolation task matching (#5288)
Added local build instructions to Readme (#5299)
Added examples for reset-batch and batch commands in help usage section (#5302)
Record current worker Identity on Pending activity tasks (#5307)
Support invoking RPC using HTTP and JSON (#5305)
Added Worklfow start metric (#5289)
Added count of workflows indicator when running the listall command and waiting it to complete (#5309)
Added option to pass consistency level in the cassandra schema version validation (#5327)

### Fixed
Fixed rendering for isolation-groups in the CLI (#5285)
Fixed SearchAfter usage (#5311)
Fixed garbage collection logic for matching tasks (#5355)
Do not make poller crash if isolation group is invalid (#5372)

### Changed
Removed unused metric (#5292)
Show error message if requesting workflow does not exist (#5300)
Parse JWT flags when creating a context (#5296)
Set ReplicatorCacheCapacity to 0 (#5301)
Show explicit message if command is not found (#5298)
IDL update to include new field in PendingActivityInfo (#5306)
Set 12.4 version for postgres containers (#5326)
Extract EventColorFunction from ColorEvent (#5321)
Update consistency level for cassandra visibility (#5330)
Improve async-matching performance for isolation (#5363)

## [1.1.0] - 2023-08-24
### Added
Added metrics for delete workflow execution on a shard level (#5126)
Added overall persistence count for shardid (#5134)
Added Scanner to purge deprecated domain workflows (#5125)
Added domain status check in taskfilter (#5140)
Added usage for InactiveDomain Invariant (#5144, #5213)
Added request body into Attributes for auditing purpose with PII (#5151)
Added remaining persistence metrics that goes to a shard #5142
Added consistent query pershard metric (#5143, #5170)
Added logging with workflow/domain tags (#5159)
Added ShardID to valid attributes (#5161)
Added Pinot docker files, table config and schema (#5163)
Added Canary TLS support (#5086)
Added a small test to catch issues with deadlocks (#5171)
Added large workflow hot shard detection (#5166)
Added thin ES clients (#5162, #5217)
Added generic ES query building utilities (#5168)
Added Physical sharding for NoSQL-based persistence (#5187)
Added tasklist traffic metrics for non-sticky and non-forwarded tasklists (#5218, #5235)
Added default value for shard_id and update_time in mysql (#5246)
Added default value for shard_id and update_time in postgres (#5259)
Added Hostname tag into metrics and other services (#5245)
Added Domain name validation (#5250)
Added isolation-group types (#5260)
Added Dynamic-config type (#5261)
Added isolation groups to persistence (#5270)
Added helper function to store/retrieve partition config from context (#5195)
Added domain handler changes for isolation group (#5274)
Added isolation-group and partition libraries (#5262)
Added resource implmentation (#5278)
Added Admin API for zonal-isolation drain commands (#5282)
Added cli operations for the zonal-isolation drains (#5283)
Added metric for isolation task matching (#5288)
Added some more coverage to isolation-group state handler (#5304)

### Fixed
Removed circular dependencies between matching components (#5111)
Fixed InsertTasks query for Cassandra (#5119)
Fixed prometheus frontend label inconsistencies (#5087)
Fixed samples documentation (#5088)
Fixed type validation in configstore DC client value updating (#5110)
Fixed the config-store handling for not-found errors (#5203)
Fixed docker (#5244)
Fixed thrift mapper for DomainConfiguration (#5268)
Fixed panic while parsing workflows with timeouts (#5267)
Fixed sticky tasklist isolation (#5308)
Fixed SearchAfter usage (#5311)
Fixed isolation groups domain drains (#5315)

### Changed
Indexer: refactor ES processor (#5100)
Moved sample logger into persistence metric client for cleaness (#5129)
ES: do not set _type when using Bulk API for v7 client (#5104)
ES: single interface for different ES/OpenSearch versions (#5158)
ES: reduce code duplication (#5137)
Updated README.md (#5064, #5251)
Set poll interval for filebased dynamic config if not set (#5160)
Upgraded Golang base image to 1.18 to remediate CVEs (#5035)
Refactor matching integration test (#5182)
Merge Activity and Decision matching tests (#5186)
Update idls version (#5200)
Allow registering search attributes without Advance Visibility enabled (#5185)
Scaffold config store for SQL (#5239)
Bench: possibility to pass frontend address using env (#5113)
Remove tcheck dependency (#5247)
Update internal type to adopt idl change (#5253)
Update persistence layer to adopt idl update for isolation (#5254)
Update history to persist partition config (#5257)
Upgrades IDL to include isolation-groups (#5258)
Make ESClient fields public (#5269)
Remove unneeded file (#5276)
Updated frontend to adopt draining isolation groups (#5225) (#5281)
Updated matching to support tasklist isolation (#5280)
Bumping version to 1.1.0 (#5284)
Improvements on tasklist isolation (#5291)
Task processing panic handling (#5294)
Update ClusterNameForFailoverVersion to return error (#5293)
Feature/isolation group library logging improvements (#5295)
Increase number of forward tokens for isolation tasklists (#5310)
Seperate token pools for tasklists with isolation (#5314)
Disable isolation for sticky tasklist (#5319)
Change default value of AsyncTaskDispatchTimeout (#5320)

## [1.0.0] - 2023-04-26
See [Release Note](https://github.com/uber/cadence/releases/tag/v1.0.0)

## [0.23.1] - 2021-11-18
See [Release Note](https://github.com/uber/cadence/releases/tag/v0.23.1)

## [0.21.3] - 2021-07-17
### Added
- Added GRPC support. Cadence server will accept requests on both TChannel and GRPC. With dynamic config flag `system.enableGRPCOutbound` it will also switch to GRPC communication internally between server components.

### Fixed
- This change contains breaking change on user config. The masterClusterName config key is deprecated and is replaced with primaryClusterName key. (#4185)

### Changed
- Bump CLI version to v0.19.0
- Change `--connect-attributes` in `cadence-sql-tool` from URL encoding to the format of k1=v1,k2=v2...
- Change `--domain_data` in `cadence domain update/register` from the format of k1:v1,k2:v2... to the format of k1=v1,k2=v2...
- Deprecate local domains. All new domains should be created as global domains.
- Server will deep merge configuration files when loading. No need to copy the whole config section, specify only those fields that needs overriding. (#4165)

## [0.18.0] - 2021-01-22

## [0.16.1] - 2021-01-21

## [0.17.0] - 2021-01-13

## [0.16.0] - 2020-12-10
