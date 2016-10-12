:toc: macro
:toc-title:

Overview
----

=== Media Type

The API uses *JSON* to communicate with clients.

You _should_ add the following accept header to your requests:

----
Accept: application/json
----

When you send JSON data with a `POST` or `PUT` request, you _must_ add the following content type header:

----
Content-Type: application/json
----

=== Tenant Header

Hawkular APM is a multi-tenant system. Your requests to tenant-dependent resources must include
a tenant header:

----
Hawkular-Tenant: my-tenant
----

=== Timestamps

The API understands all timestamps as milliseconds since January 1, 1970, 00:00:00 UTC.

=== Response codes

Resources in the API follow response codes conventions, listed below.

.Response codes conventions
[cols="30,70a", options="header"]
|===
|Response code |Meaning

|200 Ok
|The operation completed successfully.

|201 Created
|A `POST` or `PUT` operation to create an entity completed successfully.
The reponse should contain a `Location` header.

|204 No Content
|The operation completed successfully but result entity is null (`object`) or empty (`array`).
Empty arrays are not sent in the response body.

|400 Bad Request
|The operation could not be processed. It could be due to:

* Missing or malformed request entity
* Missing header/query parameter
* Malformed path/header/query parameter
* Invalid parameters (breaking business rules)

|404 Not Found
|Resource denoted by the URI does not exist.

|405 Method Not Allowed
|Resource denoted by the URI does not support the operation type.

|406 Not Acceptable
|Cannot reply in a format accepted by the client (specified in `Accept` request header).

|409 Conflict
|A `POST` or `PUT` operation could not be performed because it conflicts with an existing entity.

|415 Unsupported Media Type
|Invalid request entity format. For example, `text/plain` whereas `application/json` is expected.

|500 Internal Server Error
|Resource operation failed unexpectedly.

|503 Service Unavailable
|The server failed to initialize or the storage backend is not ready yet.
|===

=== Error responses

Error responses may include an <<ApiError>> entity in the body.

.Sample error entity
[source,javascript]
----
{"errorMsg":"Tenant is not specified. Use 'Hawkular-Tenant' header."}
----



== Base Path
`/hawkular/apm/`

== REST APIs


=== analytics
. link:#++GET__analytics_boundendpoints__name_++[Identify the bound endpoints for a business transaction]
. link:#++GET__analytics_communication_summary++[Get the trace communication summary statistics associated with criteria]
. link:#++GET__analytics_hostnames++[Get the host names associated with the criteria]
. link:#++GET__analytics_node_statistics++[Get the trace node timeseries statistics associated with criteria]
. link:#++GET__analytics_node_summary++[Get the trace node summary statistics associated with criteria]
. link:#++GET__analytics_principals++[Get principal information]
. link:#++GET__analytics_properties++[Get property information]
. link:#++GET__analytics_trace_completion_count++[Get the trace completion count]
. link:#++GET__analytics_trace_completion_faultcount++[Get the number of trace instances that returned a fault]
. link:#++GET__analytics_trace_completion_faults++[Get the trace completion fault details associated with criteria]
. link:#++GET__analytics_trace_completion_percentiles++[Get the trace completion percentiles associated with criteria]
. link:#++GET__analytics_trace_completion_property__property_++[Get the trace completion property details associated with criteria]
. link:#++GET__analytics_trace_completion_statistics++[Get the trace completion timeseries statistics associated with criteria]
. link:#++GET__analytics_trace_completion_times++[Get the trace completion times associated with criteria]
. link:#++GET__analytics_transactions++[Get transaction information]
. link:#++GET__analytics_unboundendpoints++[Identify the unbound endpoints]


==============================================

[[GET__analytics_boundendpoints__name_]]
*Endpoint GET `/analytics/boundendpoints/{name}`*

NOTE: *Identify the bound endpoints for a business transaction* +




*Path parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|name|Yes|business transaction name|string|-|-

|=======================



*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|startTime|No|optional 'start' time, default 1 hour before current time|integer|int64|-
|endTime|No|optional 'end' time, default current time|integer|int64|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_communication_summary]]
*Endpoint GET `/analytics/communication/summary`*

NOTE: *Get the trace communication summary statistics associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|tree|No|tree|boolean|-|-
|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_hostnames]]
*Endpoint GET `/analytics/hostnames`*

NOTE: *Get the host names associated with the criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_node_statistics]]
*Endpoint GET `/analytics/node/statistics`*

NOTE: *Get the trace node timeseries statistics associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|interval|No|-|integer|int64|-
|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_node_summary]]
*Endpoint GET `/analytics/node/summary`*

NOTE: *Get the trace node summary statistics associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_principals]]
*Endpoint GET `/analytics/principals`*

NOTE: *Get principal information* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_properties]]
*Endpoint GET `/analytics/properties`*

NOTE: *Get property information* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_trace_completion_count]]
*Endpoint GET `/analytics/trace/completion/count`*

NOTE: *Get the trace completion count* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|integer
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_trace_completion_faultcount]]
*Endpoint GET `/analytics/trace/completion/faultcount`*

NOTE: *Get the number of trace instances that returned a fault* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|integer
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_trace_completion_faults]]
*Endpoint GET `/analytics/trace/completion/faults`*

NOTE: *Get the trace completion fault details associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_trace_completion_percentiles]]
*Endpoint GET `/analytics/trace/completion/percentiles`*

NOTE: *Get the trace completion percentiles associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|<<Percentiles>>
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_trace_completion_property__property_]]
*Endpoint GET `/analytics/trace/completion/property/{property}`*

NOTE: *Get the trace completion property details associated with criteria* +




*Path parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|property|No|property|string|-|-

|=======================



*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_trace_completion_statistics]]
*Endpoint GET `/analytics/trace/completion/statistics`*

NOTE: *Get the trace completion timeseries statistics associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|interval|No|-|integer|int64|-
|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_trace_completion_times]]
*Endpoint GET `/analytics/trace/completion/times`*

NOTE: *Get the trace completion times associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_transactions]]
*Endpoint GET `/analytics/transactions`*

NOTE: *Get transaction information* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__analytics_unboundendpoints]]
*Endpoint GET `/analytics/unboundendpoints`*

NOTE: *Identify the unbound endpoints* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|startTime|No|optional 'start' time, default 1 hour before current time|integer|int64|-
|endTime|No|optional 'end' time, default current time|integer|int64|-
|compress|No|compress list to show common patterns|boolean|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================


=== config
. link:#++GET__config_businesstxn_full++[Retrieve the business transaction configurations, changed since an optional specified time]
. link:#++POST__config_businesstxn_full++[Add or update the business transaction configurations]
. link:#++DELETE__config_businesstxn_full__name_++[Remove the business transaction configuration with the specified name]
. link:#++GET__config_businesstxn_full__name_++[Retrieve the business transaction configuration for the specified name]
. link:#++PUT__config_businesstxn_full__name_++[Add or update the business transaction configuration for the specified name]
. link:#++GET__config_businesstxn_summary++[Retrieve the business transaction summaries]
. link:#++POST__config_businesstxn_validate++[Validate the business transaction configuration]
. link:#++GET__config_collector++[Retrieve the collector configuration for the optionally specified host and server]


==============================================

[[GET__config_businesstxn_full]]
*Endpoint GET `/config/businesstxn/full`*

NOTE: *Retrieve the business transaction configurations, changed since an optional specified time* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|updated|No|updated since|integer|int64|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[POST__config_businesstxn_full]]
*Endpoint POST `/config/businesstxn/full`*

NOTE: *Add or update the business transaction configurations* +




*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[DELETE__config_businesstxn_full__name_]]
*Endpoint DELETE `/config/businesstxn/full/{name}`*

NOTE: *Remove the business transaction configuration with the specified name* +




*Path parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|name|Yes|business transaction name|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|-
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__config_businesstxn_full__name_]]
*Endpoint GET `/config/businesstxn/full/{name}`*

NOTE: *Retrieve the business transaction configuration for the specified name* +




*Path parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|name|Yes|business transaction name|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|<<BusinessTxnConfig>>
|500|Internal server error|-

|=======================



==============================================




==============================================

[[PUT__config_businesstxn_full__name_]]
*Endpoint PUT `/config/businesstxn/full/{name}`*

NOTE: *Add or update the business transaction configuration for the specified name* +




*Path parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|name|Yes|business transaction name|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__config_businesstxn_summary]]
*Endpoint GET `/config/businesstxn/summary`*

NOTE: *Retrieve the business transaction summaries* +




*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[POST__config_businesstxn_validate]]
*Endpoint POST `/config/businesstxn/validate`*

NOTE: *Validate the business transaction configuration* +




*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|array of object
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__config_collector]]
*Endpoint GET `/config/collector`*

NOTE: *Retrieve the collector configuration for the optionally specified host and server* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|type|No|optional type|string|-|-
|host|No|optional host name|string|-|-
|server|No|optional server name|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|<<CollectorConfiguration>>
|500|Internal server error|-

|=======================



==============================================


=== traces
. link:#++GET__traces_complete__id_++[Retrieve end to end trace for specified id]
. link:#++POST__traces_fragments++[Add a list of trace fragments]
. link:#++GET__traces_fragments_search++[Query trace fragments associated with criteria]
. link:#++GET__traces_fragments__id_++[Retrieve trace fragment for specified id]


==============================================

[[GET__traces_complete__id_]]
*Endpoint GET `/traces/complete/{id}`*

NOTE: *Retrieve end to end trace for specified id* +




*Path parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|id|Yes|id of required record|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success, trace found and returned|<<Trace>>
|404|Unknown trace id|-
|500|Internal server error|-

|=======================



==============================================




==============================================

[[POST__traces_fragments]]
*Endpoint POST `/traces/fragments`*

NOTE: *Add a list of trace fragments* +




*Body*

[cols="^20,55,^25", options="header"]
|=======================
|Required|Description|Data Type

|Yes|List of traces|array of <<Trace>>

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Adding traces succeeded.|-
|500|Unexpected error happened while storing the trace fragments|-

|=======================



==============================================




==============================================

[[GET__traces_fragments_search]]
*Endpoint GET `/traces/fragments/search`*

NOTE: *Query trace fragments associated with criteria* +




*Query parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|criteria|No|-|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success|<<Trace>>
|500|Internal server error|-

|=======================



==============================================




==============================================

[[GET__traces_fragments__id_]]
*Endpoint GET `/traces/fragments/{id}`*

NOTE: *Retrieve trace fragment for specified id* +




*Path parameters*

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Parameter|Required|Description|Type|Format|Allowable Values

|id|Yes|id of required record|string|-|-

|=======================



*Response*

*Status codes*
[cols="^20,55,^25", options="header"]
|=======================
|Status Code|Reason|Response Model

|200|Success, trace found and returned|<<Trace>>
|404|Unknown fragment id|-
|500|Internal server error|-

|=======================



==============================================


== Data Types



[[AddContentAction]]
=== AddContentAction

Inherits: <<ProcessorAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|expression|No|-|<<Expression>>|-|-
|name|No|-|string|-|-
|type|No|-|string|-|-

|=======================


[[AddCorrelationIdAction]]
=== AddCorrelationIdAction

Inherits: <<ProcessorAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|expression|No|-|<<Expression>>|-|-
|scope|No|-|string|-|Interaction, ControlFlow, CausedBy

|=======================


[[AssertComplete]]
=== AssertComplete

Inherits: <<InstrumentAction>>

[[BusinessTxnConfig]]
=== BusinessTxnConfig


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|deleted|No|-|boolean|-|-
|description|No|-|string|-|-
|filter|No|-|<<Filter>>|-|-
|lastUpdated|No|-|integer|int64|-
|level|No|-|string|-|Ignore, None, All
|processors|No|-|array of <<Processor>>|-|-

|=======================


[[CollectorConfiguration]]
=== CollectorConfiguration


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|businessTransactions|No|-|object|-|-
|instrumentation|No|-|object|-|-
|properties|No|-|object|-|-

|=======================


[[CompleteCorrelation]]
=== CompleteCorrelation

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|allowSpawn|No|-|boolean|-|-
|idExpression|No|-|string|-|-

|=======================


[[Component]]
=== Component

Inherits: <<InteractionNode>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|componentType|No|-|string|-|-

|=======================


[[Consumer]]
=== Consumer

Inherits: <<InteractionNode>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|endpointType|No|-|string|-|-

|=======================


[[ContainerNode]]
=== ContainerNode

Inherits: <<Node>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|nodes|No|-|array of <<Node>>|-|-

|=======================


[[Content]]
=== Content


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|type|No|-|string|-|-
|value|No|-|string|-|-

|=======================


[[Correlate]]
=== Correlate

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|idExpression|No|-|string|-|-

|=======================


[[CorrelationIdentifier]]
=== CorrelationIdentifier


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|scope|No|-|string|-|Interaction, ControlFlow, CausedBy
|value|No|-|string|-|-

|=======================


[[Deactivate]]
=== Deactivate

Inherits: <<InstrumentAction>>

[[EvaluateURIAction]]
=== EvaluateURIAction

Inherits: <<ProcessorAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|template|No|-|string|-|-

|=======================


[[Expression]]
=== Expression


[[Filter]]
=== Filter


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|exclusions|No|-|array of string|-|-
|inclusions|No|-|array of string|-|-

|=======================


[[FreeFormAction]]
=== FreeFormAction

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|action|No|-|string|-|-

|=======================


[[IgnoreNode]]
=== IgnoreNode

Inherits: <<InstrumentAction>>

[[InitiateCorrelation]]
=== InitiateCorrelation

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|idExpression|No|-|string|-|-

|=======================


[[InstrumentAction]]
=== InstrumentAction


[[InstrumentBind]]
=== InstrumentBind


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|expression|No|-|string|-|-
|name|No|-|string|-|-
|type|No|-|string|-|-

|=======================


[[InstrumentComponent]]
=== InstrumentComponent

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|componentTypeExpression|No|-|string|-|-
|direction|No|-|string|-|In, Out
|idExpression|No|-|string|-|-
|operationExpression|No|-|string|-|-
|uriExpression|No|-|string|-|-

|=======================


[[InstrumentConsumer]]
=== InstrumentConsumer

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|direction|No|-|string|-|In, Out
|endpointTypeExpression|No|-|string|-|-
|idExpression|No|-|string|-|-
|operationExpression|No|-|string|-|-
|uriExpression|No|-|string|-|-

|=======================


[[InstrumentProducer]]
=== InstrumentProducer

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|direction|No|-|string|-|In, Out
|endpointTypeExpression|No|-|string|-|-
|idExpression|No|-|string|-|-
|operationExpression|No|-|string|-|-
|uriExpression|No|-|string|-|-

|=======================


[[InstrumentRule]]
=== InstrumentRule


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|notes|No|-|array of string|-|-
|ruleName|No|-|string|-|-

|=======================


[[Instrumentation]]
=== Instrumentation


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|compile|No|-|boolean|-|-
|description|No|-|string|-|-
|rules|No|-|array of <<InstrumentRule>>|-|-

|=======================


[[InteractionNode]]
=== InteractionNode

Inherits: <<ContainerNode>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|in|No|-|<<Message>>|-|-
|out|No|-|<<Message>>|-|-

|=======================


[[Issue]]
=== Issue


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|description|No|-|string|-|-
|severity|No|-|string|-|Error, Warning, Info

|=======================


[[JSONExpression]]
=== JSONExpression

Inherits: <<Expression>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|jsonpath|No|-|string|-|-
|key|No|-|string|-|-
|source|No|-|string|-|Content, Header

|=======================


[[JVM]]
=== JVM

Inherits: <<InstrumentRule>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|actions|No|-|array of <<InstrumentAction>>|-|-
|binds|No|-|array of <<InstrumentBind>>|-|-
|className|No|-|string|-|-
|compile|No|-|boolean|-|-
|condition|No|-|string|-|-
|fromVersion|No|-|string|-|-
|helper|No|-|string|-|-
|interfaceName|No|-|string|-|-
|location|No|-|string|-|-
|methodName|No|-|string|-|-
|parameterTypes|No|-|array of string|-|-
|toVersion|No|-|string|-|-

|=======================


[[LiteralExpression]]
=== LiteralExpression

Inherits: <<Expression>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|value|No|-|string|-|-

|=======================


[[Message]]
=== Message


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|content|No|-|object|-|-
|headers|No|-|object|-|-

|=======================


[[Node]]
=== Node


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|baseTime|No|-|integer|int64|-
|correlationIds|No|-|array of <<CorrelationIdentifier>>|-|-
|details|No|-|object|-|-
|duration|No|-|integer|int64|-
|issues|No|-|array of <<Issue>>|-|-
|operation|No|-|string|-|-
|properties|No|-|array of <<Property>>|-|-
|type|No|-|string|-|Consumer, Producer, Component
|uri|No|-|string|-|-

|=======================


[[Percentiles]]
=== Percentiles


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|percentiles|No|-|object|-|-

|=======================


[[ProcessContent]]
=== ProcessContent

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|direction|No|-|string|-|In, Out
|valueExpressions|No|-|array of string|-|-

|=======================


[[ProcessHeaders]]
=== ProcessHeaders

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|direction|No|-|string|-|In, Out
|headersExpression|No|-|string|-|-
|originalType|No|-|string|-|-

|=======================


[[Processor]]
=== Processor


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|actions|No|-|array of <<ProcessorAction>>|-|-
|description|No|-|string|-|-
|direction|No|-|string|-|In, Out
|faultFilter|No|-|string|-|-
|nodeType|No|-|string|-|Consumer, Producer, Component
|operation|No|-|string|-|-
|predicate|No|-|<<Expression>>|-|-
|uriFilter|No|-|string|-|-

|=======================


[[ProcessorAction]]
=== ProcessorAction


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|description|No|-|string|-|-
|predicate|No|-|<<Expression>>|-|-

|=======================


[[ProcessorIssue]]
=== ProcessorIssue

Inherits: <<Issue>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|action|No|-|string|-|-
|field|No|-|string|-|-
|processor|No|-|string|-|-

|=======================


[[Producer]]
=== Producer

Inherits: <<InteractionNode>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|endpointType|No|-|string|-|-

|=======================


[[Property]]
=== Property


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|name|No|-|string|-|-
|number|No|-|number|double|-
|type|No|-|string|-|Text, Number, Boolean, Binary
|value|No|-|string|-|-

|=======================


[[SetBusinessTransaction]]
=== SetBusinessTransaction

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|nameExpression|No|-|string|-|-

|=======================


[[SetDetail]]
=== SetDetail

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|name|No|-|string|-|-
|nodeType|No|-|string|-|-
|onStack|No|-|boolean|-|-
|valueExpression|No|-|string|-|-

|=======================


[[SetDetailAction]]
=== SetDetailAction

Inherits: <<ProcessorAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|expression|No|-|<<Expression>>|-|-
|name|No|-|string|-|-

|=======================


[[SetFault]]
=== SetFault

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|valueExpression|No|-|string|-|-

|=======================


[[SetFaultAction]]
=== SetFaultAction

Inherits: <<ProcessorAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|expression|No|-|<<Expression>>|-|-

|=======================


[[SetLevel]]
=== SetLevel

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|levelExpression|No|-|string|-|-

|=======================


[[SetPrincipal]]
=== SetPrincipal

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|nameExpression|No|-|string|-|-

|=======================


[[SetProperty]]
=== SetProperty

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|name|No|-|string|-|-
|valueExpression|No|-|string|-|-

|=======================


[[SetPropertyAction]]
=== SetPropertyAction

Inherits: <<ProcessorAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|expression|No|-|<<Expression>>|-|-
|name|No|-|string|-|-
|type|No|-|string|-|Text, Number, Boolean, Binary

|=======================


[[SetState]]
=== SetState

Inherits: <<InstrumentAction>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|contextExpression|No|-|string|-|-
|name|No|-|string|-|-
|session|No|-|boolean|-|-
|valueExpression|No|-|string|-|-

|=======================


[[Suppress]]
=== Suppress

Inherits: <<InstrumentAction>>

[[TextExpression]]
=== TextExpression

Inherits: <<Expression>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|key|No|-|string|-|-
|source|No|-|string|-|Content, Header

|=======================


[[Trace]]
=== Trace


[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|businessTransaction|No|-|string|-|-
|hostAddress|No|-|string|-|-
|hostName|No|-|string|-|-
|id|No|-|string|-|-
|nodes|No|-|array of <<Node>>|-|-
|principal|No|-|string|-|-
|startTime|No|-|integer|int64|-

|=======================


[[Unlink]]
=== Unlink

Inherits: <<InstrumentAction>>

[[XMLExpression]]
=== XMLExpression

Inherits: <<Expression>>

[cols="15,^10,35,^15,^10,^15", options="header"]
|=======================
|Name|Required|Description|Type|Format|Allowable Values

|key|No|-|string|-|-
|source|No|-|string|-|Content, Header
|xpath|No|-|string|-|-

|=======================