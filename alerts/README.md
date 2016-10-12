:imagesdir: ../images

:toc: macro
:toc-title:

= Managing Alerts

=== Hawkular Services
Hawkular Alerts is an alert engine that is distributed as part of http://www.hawkular.org[Hawkular Services].

Information on how to install and run Hawkular Services can be found on the http://www.hawkular.org/hawkular-services/docs/installation-guide[Hawkular website].

Use of Hawkular Alerts is currently via its REST API. Information on this API can be found http://www.hawkular.org/docs/rest/rest-alerts.html[here].

=== Configuring APM to send events to Hawkular Alerts

Hawkular APM can be configured to send events to Hawkular Alerts, to be evaluated based on trigger conditions configured by the end user.

Prior to starting the Hawkular APM server, the following environment variables should be specified:

|===
| Name | Description
| HAWKULAR_URI | The URL of the Hawkular Services server
| HAWKULAR_USERNAME | The username for authenticating against the Hawkular Services server
| HAWKULAR_PASSWORD | The password for authenticating against the Hawkular Services server
|===

=== Event Types

All events generated from Hawkular APM will have the following fields in common:

* The _dataId_ will represent the event type
* The _dataSource_ will represent the hostname where the event originated. For some events, this may not be relevant (i.e. if associated with multiple hosts) and therefore will be left blank
* The _category_ will always be `APM`

Currently Hawkular APM will send the following events to the Alerts engine:

===== Trace Completion Time

The dataId for this event type is `TraceCompletionTime`.

These events represent the completion time associated with an end to end trace instance (i.e. a business transaction instance).

For example, if an end user invokes your application to place an order, and that request results in various messages being passed between your backend services (e.g. inventory, credit checking, customer service, etc) then all of these subsequent service invocations are associated with a single trace instance triggered by the initial user request.

The event will also include any properties that are associated with the trace instance defined as tags. If a property had multiple values, then the tag will have a comma separated list of those values.




