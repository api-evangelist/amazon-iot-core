# AWS IoT Core GraphQL Schema

## Overview

This GraphQL schema provides a conceptual representation of the [AWS IoT Core REST API](https://docs.aws.amazon.com/iot/latest/apireference/). It covers the full surface of IoT device connectivity and management, including thing registry, certificates, policies, device shadows, topic rules, jobs, fleet indexing, authorizers, security profiles, auditing, mitigation actions, CA certificates, and provisioning templates.

The schema is derived from the AWS IoT Core API reference and is intended to illustrate how the REST API resources and operations map to a GraphQL type system.

## Schema Source

- **Provider:** Amazon Web Services (AWS)
- **Service:** AWS IoT Core
- **API Reference:** https://docs.aws.amazon.com/iot/latest/apireference/
- **Base URL:** https://iot.amazonaws.com
- **Schema File:** amazon-iot-core-schema.graphql

## Type Coverage

The schema defines 70+ named types organized across the following domains:

### Thing Registry
- `Thing` — core IoT device record with name, ARN, type, and attributes
- `ThingDetails` — extended thing description including default client ID
- `ThingType` — thing type with searchable attributes and metadata
- `ThingTypeProperties` / `ThingTypeMetadata` — type definition details
- `ThingGroup` / `ThingGroupDetails` — hierarchical device grouping
- `ThingAttribute` — key/value attribute pairs for things
- `GroupNameAndArn` — group reference used in list responses
- `ThingConnectivity` — device connectivity state and timestamp

### Certificates
- `Certificate` — certificate summary with ID, ARN, and status
- `CertificateDetails` — full certificate record including PEM and transfer data
- `CertificateStatus` (enum) — ACTIVE, INACTIVE, REVOKED, PENDING_TRANSFER, REGISTER_INACTIVE, PENDING_ACTIVATION
- `TransferData` — certificate transfer request details
- `CertificateValidity` — notBefore / notAfter validity window

### Policies
- `Policy` — policy name and ARN
- `PolicyDetails` — policy document and default version
- `PolicyVersion` — versioned policy document with default flag

### Principals and Attachments
- `Principal` — certificate or identity attached to a thing or policy
- `Attachment` — thing-to-principal or thing-to-policy relationship record

### Device Shadows
- `Shadow` — shadow summary for a thing
- `ShadowDetails` — full shadow document with state, metadata, version, and timestamp
- `ShadowState` — container for desired, reported, and delta documents
- `Desired` / `Reported` / `Delta` — shadow state document sections
- `NamedShadow` / `NamedShadowDetails` — named (non-classic) shadow records

### Messaging
- `Message` — MQTT message payload with topic and QoS
- `MessageDetails` — extended message including client ID and timestamp
- `MessageBroker` — MQTT broker endpoint descriptor

### Topics and Rules
- `Topic` / `TopicDetails` — MQTT topic pattern descriptors
- `TopicRule` — IoT Rules Engine rule with SQL, actions, and error action
- `TopicRuleDestination` — HTTP or VPC destination for rule forwarding
- `HttpUrlDestinationProperties` / `VpcDestinationProperties` — destination config
- `RuleAction` — union container for all supported rule action types
- `SNSAction` / `SQSAction` / `DynamoDBAction` / `LambdaAction` / `S3Action` — core rule actions
- `IoTAnalyticsAction` / `RepublishAction` / `KinesisAction` / `FirehoseAction` / `CloudwatchMetricAction` — extended rule actions

### Jobs
- `Job` — job summary with ID, status, targets, and timestamps
- `JobDetails` — full job record including document, rollout, abort, and timeout config
- `JobStatus` (enum) — IN_PROGRESS, CANCELED, COMPLETED, DELETION_IN_PROGRESS, SCHEDULED
- `JobExecution` — per-device job execution record
- `JobExecutionStatus` (enum) — QUEUED, IN_PROGRESS, FAILED, SUCCESS, CANCELED, TIMED_OUT, REJECTED, REMOVED
- `JobDocument` — job document or S3 source reference
- `PresignedUrlConfig` — pre-signed URL expiry for job documents
- `JobExecutionsRolloutConfig` / `ExponentialRolloutRate` / `RateIncreaseCriteria` — rollout controls
- `AbortConfig` / `AbortCriteria` — job abort thresholds
- `TimeoutConfig` — in-progress timeout in minutes

### Fleet and Indexing
- `Fleet` / `FleetDetails` — fleet metric definitions for aggregated device telemetry
- `AggregationType` — aggregation type and values for fleet metrics
- `IndexSearch` — search result record from the thing indexer
- `SearchIndex` — index descriptor (name, status, schema)
- `ThingConnectivity` — live connectivity state from the index

### Authorizers
- `Authorizer` — custom authorizer name and ARN
- `AuthorizerDetails` — full authorizer config with Lambda ARN, token key, signing keys, and caching

### Security Profiles (Detect)
- `SecurityProfile` / `SecurityProfileDetails` — Detect security profile and its behaviors
- `Behavior` — individual behavior definition within a profile
- `MetricDimension` / `BehaviorCriteria` — behavior criteria components
- `MetricValue` — threshold value for behavior comparisons
- `StatisticalThreshold` / `MachineLearningDetectionConfig` — advanced detection config
- `Metric` / `MetricToRetain` — custom and retained metrics

### Audit
- `Audit` — audit task summary
- `AuditTask` — detailed audit task with statistics
- `AuditTaskStatistics` — check counts by outcome
- `AuditFinding` — individual non-compliant finding from an audit check

### Mitigation
- `Mitigation` — mitigation task applied to audit findings
- `MitigationAction` — reusable mitigation action definition
- `MitigationActionParams` — union of all action parameter types
- `UpdateDeviceCertificateParams` / `UpdateCACertificateParams` / `AddThingsToThingGroupParams` / `ReplaceDefaultPolicyVersionParams` / `EnableIoTLoggingParams` / `PublishFindingToSnsParams` — individual action parameter types

### CA Certificates
- `CA` — CA certificate record with status, auto-registration, and validity

### Provisioning
- `ProvisioningTemplate` — fleet provisioning template with body and hook
- `ProvisioningHook` — Lambda hook invoked before provisioning

### Auth / Tokens
- `APIKey` — API key reference
- `Token` — short-lived credential token
- `Webhook` — webhook endpoint registration

### Scalars
- `AWSDateTime` — ISO 8601 date-time string
- `AWSJSON` — arbitrary JSON document
- `AWSTimestamp` — Unix epoch timestamp (milliseconds)

## Operations

### Queries
The schema exposes read operations across all resource types, including:
- Single-resource describe operations (e.g., `getThing`, `describeCertificate`, `describeJob`)
- List operations with pagination via `nextToken` or `marker` cursors
- Search via `searchIndex` using IoT fleet indexing query strings

### Mutations
Write operations include:
- CRUD for things, thing types, and thing groups
- Certificate registration, status updates, and deletion
- Policy creation, versioning, attachment, and detachment
- Shadow updates and deletion
- Topic rule creation, toggling, and deletion
- Job creation and cancellation
- Security profile and mitigation action management
- Provisioning template lifecycle

## Notes

- This is a conceptual schema; AWS IoT Core does not natively expose a GraphQL endpoint.
- The schema follows AWS IoT Core API conventions from the official REST API reference.
- Pagination uses `nextToken` (most resources) or `marker` (certificates and policies) consistent with the REST API.
- Certain complex policy and shadow document fields are typed as `AWSJSON` to preserve fidelity with the REST API's raw JSON payloads.
