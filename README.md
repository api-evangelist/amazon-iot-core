# Amazon IoT Core (amazon-iot-core)
AWS IoT Core is a managed cloud service that lets connected devices easily and securely interact with cloud applications and other devices. It can support billions of devices and trillions of messages, routing those messages to AWS endpoints and other devices reliably and securely.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/amazon-iot-core/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - AWS, Device Management, IoT, MQTT, Message Routing

## Timestamps

- **Created:** 2026-03-16
- **Modified:** 2026-04-19

## APIs

### AWS IoT Core API
The AWS IoT Core API provides programmatic access to manage things, policies, certificates, rules, and MQTT messaging for IoT device connectivity.

**Human URL:** [https://aws.amazon.com/iot-core/](https://aws.amazon.com/iot-core/)

#### Tags:

 - Device Management, IoT, MQTT

#### Properties

- [Documentation](https://docs.aws.amazon.com/iot/latest/apireference/)
- [OpenAPI](openapi/amazon-iot-core-openapi-original.yml)
- [GettingStarted](https://docs.aws.amazon.com/iot/latest/developerguide/iot-gs.html)
- [Pricing](https://aws.amazon.com/iot-core/pricing/)
- [FAQ](https://aws.amazon.com/iot-core/faqs/)

## Common Properties

- [Portal](https://aws.amazon.com/iot-core/)
- [Website](https://aws.amazon.com/iot-core/)
- [Documentation](https://docs.aws.amazon.com/iot/)
- [TermsOfService](https://aws.amazon.com/service-terms/)
- [PrivacyPolicy](https://aws.amazon.com/privacy/)
- [Support](https://aws.amazon.com/premiumsupport/)
- [Blog](https://aws.amazon.com/blogs/iot/)
- [GitHubOrganization](https://github.com/aws)
- [Console](https://console.aws.amazon.com/iot/)
- [SignUp](https://portal.aws.amazon.com/billing/signup)
- [Login](https://signin.aws.amazon.com/)
- [StatusPage](https://health.aws.amazon.com/health/status)
- [Contact](https://aws.amazon.com/contact-us/)

## Features

| Name | Description |
|------|-------------|
| Secure Device Connectivity | Connects IoT devices to AWS using MQTT, HTTPS, and WebSocket protocols with mutual TLS authentication. |
| Message Broker | Scales to billions of messages per day with a fully managed MQTT message broker. |
| Rules Engine | Routes device messages to 15+ AWS services based on SQL-like rules. |
| Device Shadow | Maintains a persistent virtual representation of each device for state management. |
| Fleet Indexing | Index and search all IoT things and their attributes at scale. |

## Use Cases

| Name | Description |
|------|-------------|
| Industrial IoT | Connect factory equipment to AWS for real-time monitoring and predictive maintenance. |
| Smart Home | Build connected home devices with secure two-way communication. |
| Asset Tracking | Track vehicles, equipment, and assets with GPS and sensor data. |

## Integrations

| Name | Description |
|------|-------------|
| AWS Lambda | Trigger serverless functions from IoT device messages with Rules Engine. |
| Amazon Kinesis | Stream IoT telemetry data to Kinesis for real-time analytics. |
| Amazon S3 | Store device messages and data in S3 using IoT Rules. |
| Amazon DynamoDB | Write device state data to DynamoDB tables with IoT Rules. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [AWS IoT Core API](openapi/amazon-iot-core-openapi-original.yml)

### JSON Schema

200 schema files covering key resources and operations.

### JSON Structure

200 JSON Structure files converted from JSON Schema.

### JSON-LD

- [Amazon IoT Core Context](json-ld/amazon-iot-core-context.jsonld)

### Examples

200 example JSON files generated from schemas.

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [AWS IoT Core API](capabilities/shared/iot-core.yaml) — operations for amazon iot core management

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Iot Device Connectivity](capabilities/iot-device-connectivity.yaml) | Amazon IoT Core | 8 | IoT Developer, Solutions Architect |

## Vocabulary

- [Amazon IoT Core Vocabulary](vocabulary/amazon-iot-core-vocabulary.yaml) — Unified taxonomy mapping resources, actions, workflows, and personas

## Rules

- [Amazon IoT Core Spectral Rules](rules/amazon-iot-core-spectral-rules.yml) — 14 rules across 6 categories enforcing Amazon IoT Core API conventions

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
