# WARAS - WhatsApp Remote Automation Service

<div align="center">

**Unofficial, Lightweight, Self-Hosted WhatsApp Automation Engine built with Rust**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Rust](https://img.shields.io/badge/rust-1.75%2B-orange.svg)](https://www.rust-lang.org/)

[Purpose](#purpose) • [Core Concepts](#core-concepts) • [Use Cases](#use-cases) • [Vision](#vision) • [Roadmap](#roadmap)

</div>

---

## Purpose

WARAS (WhatsApp Remote Automation Service) is an unofficial, lightweight, self-hosted WhatsApp automation engine specifically designed as a remote API service rather than a traditional bot. The project aims to provide developers and automation enthusiasts with a high-performance, resource-efficient foundation for WhatsApp automation that can be deployed anywhere and integrated with any system.

The name WARAS reflects the core principle: a sane, rational approach to WhatsApp automation that prioritizes performance, simplicity, and self-hosting capabilities while maintaining the flexibility to evolve into a Platform-as-a-Service offering in the future.

---

## Core Concepts

### API-First Architecture

WARAS is designed from the ground up as an API service, not a standalone bot. This fundamental design decision enables:

- **Universal Integration**: Any client capable of making HTTP requests can control WhatsApp through WARAS, including workflow automation tools (n8n, Make.com), programming languages (Python, JavaScript, Go), or custom backends.

- **Separation of Concerns**: Business logic lives in your application, while WARAS handles the complexity of WhatsApp protocol implementation, encryption, and session management.

- **Stateless Operations**: Each API request is independent, allowing horizontal scaling and simplified deployment patterns.

### Self-Hosted by Default

While many WhatsApp automation solutions operate as cloud services, WARAS prioritizes self-hosting:

- **Data Sovereignty**: All WhatsApp data, sessions, and credentials remain on infrastructure you control.

- **Privacy by Design**: No third-party service has access to your messages, contacts, or authentication tokens.

- **Cost Efficiency**: Pay only for the infrastructure you use, with no per-message or per-session pricing from a SaaS provider.

- **Customization Freedom**: Modify, extend, or adapt the service to your specific requirements without vendor limitations.

### Multi-Session Architecture

Unlike traditional WhatsApp bots that manage a single connection, WARAS supports multiple concurrent WhatsApp sessions within a single service instance:

- **Resource Optimization**: Run multiple WhatsApp accounts without deploying multiple containers or processes.

- **Isolation**: Each session maintains independent state, authentication, and configuration.

- **Dynamic Management**: Sessions can be added, removed, or restarted without affecting other active sessions or requiring service restart.

### Minimal Runtime Requirements

WARAS is built with Rust to achieve exceptional performance and minimal resource consumption:

- **Low Memory Footprint**: Designed to operate efficiently even on constrained hardware.

- **Fast Startup**: Service initialization and session establishment happen in seconds, not minutes.

- **Small Container Images**: Docker images are optimized to remain under 30MB, reducing storage costs and deployment time.

- **Efficient Protocol Handling**: Native implementation of WhatsApp protocol in Rust eliminates interpreter overhead.

---

## Use Cases

### Workflow Automation

WARAS serves as a WhatsApp node in automation workflows:

- Trigger WhatsApp messages based on events from other systems (databases, APIs, webhooks)
- React to incoming WhatsApp messages and route them to appropriate handlers
- Integrate WhatsApp communication into complex multi-step automation sequences
- Build custom notification pipelines that leverage WhatsApp as one communication channel among many

### Backend Integration

Applications can delegate WhatsApp functionality to WARAS:

- E-commerce platforms sending order confirmations and shipping updates
- Customer support systems routing tickets to WhatsApp
- IoT devices sending alerts through WhatsApp when specific conditions are met
- Internal tools enabling team communication through a familiar interface

### Personal Automation

Individuals can automate their own WhatsApp usage:

- Schedule messages for future delivery
- Auto-reply to messages based on keywords or sender
- Archive or forward messages programmatically
- Sync WhatsApp data with personal knowledge management systems

### Research and Development

WARAS provides a foundation for:

- Protocol analysis and reverse engineering studies
- Security research on end-to-end encryption implementations
- Performance benchmarking of messaging protocols
- Educational projects teaching network programming and cryptography

---

## Vision

### Current State: Self-Hosted Service

WARAS currently exists as a self-hosted service that individuals and organizations can deploy on their own infrastructure. The focus is on providing a stable, performant, and well-documented API that handles the complexity of WhatsApp automation.

### Future State: Optional PaaS Layer

The long-term vision includes offering a managed Platform-as-a-Service option while maintaining full support for self-hosting:

- **Hybrid Model**: Users can choose between self-hosting (full control, one-time setup) or managed hosting (zero maintenance, pay-as-you-go).

- **Same Codebase**: The PaaS offering will run the exact same open-source code that self-hosters use, ensuring feature parity and trust.

- **Multi-Tenancy Support**: The service will evolve to support true multi-tenancy with account isolation, API key management per tenant, and usage metering.

- **Self-Host First**: Even as PaaS capabilities are added, self-hosting will remain a first-class use case with comprehensive documentation and support.

### Design Principles

**Performance Over Convenience**  
Every architectural decision prioritizes runtime performance and resource efficiency. If a feature adds significant overhead, it becomes opt-in rather than default.

**Simplicity Over Completeness**  
WARAS aims to do WhatsApp automation exceptionally well rather than attempting to be an all-in-one communication platform. Features that dilute this focus are excluded.

**Standards Over Custom Solutions**  
Where industry standards exist (OpenAPI, Prometheus metrics, standard HTTP auth), WARAS adopts them rather than inventing custom approaches.

**Observable by Default**  
Health checks, metrics, and logging are built-in from the start, not added as afterthoughts. Self-hosters should be able to monitor WARAS using standard tools.

**API Stability**  
Breaking changes to the public API are avoided whenever possible. When necessary, they follow semantic versioning and include migration guides.

---

## Roadmap

### Phase 1: Foundation (Current)

**Objective**: Establish a stable, self-hostable service with core WhatsApp functionality.

**Capabilities**:

- Authentication via QR code and phone number pairing
- Persistent session storage with automatic reconnection
- Send and receive text messages
- Media handling (upload/download images, videos, documents)
- Basic contact and group operations
- RESTful API with OpenAPI documentation
- WebSocket support for real-time events
- SQLite-based storage
- Docker deployment

**Target Audience**: Developers comfortable with API integration and self-hosting.

### Phase 2: Multi-Session Management

**Objective**: Enable managing multiple WhatsApp accounts from a single WARAS instance.

**Capabilities**:

- Session isolation and independent lifecycle management
- Web-based UI for session setup and monitoring
- API key management with per-session scoping
- Session health monitoring and automatic recovery
- Webhook delivery for incoming messages and events
- Improved documentation with integration examples

**Target Audience**: Users managing multiple WhatsApp accounts (agencies, support teams, automation power-users).

### Phase 3: Advanced Automation Features

**Objective**: Expand functionality to cover complex automation scenarios.

**Capabilities**:

- Message scheduling and delayed delivery
- Bulk messaging with rate limiting and throttling
- Advanced group management (create, modify, admin operations)
- Message templates and variable substitution
- PostgreSQL storage option for multi-instance deployments
- Redis integration for caching and pub/sub
- Enhanced filtering and routing for incoming messages

**Target Audience**: Organizations building sophisticated automation workflows.

### Phase 4: PaaS Foundation

**Objective**: Prepare architecture for optional managed hosting while maintaining self-host support.

**Capabilities**:

- Multi-tenancy with complete data isolation
- Account management and authentication systems
- Usage metering and quota enforcement
- Billing integration framework
- Cloud storage backends (S3-compatible) for session data
- Kubernetes operator for automated deployment and scaling
- Enhanced security features (audit logs, access controls)

**Target Audience**: Both self-hosters and users who prefer managed infrastructure.

### Phase 5: Ecosystem Expansion

**Objective**: Build integrations and tooling that make WARAS easier to use across platforms.

**Capabilities**:

- Native n8n node for drag-and-drop integration
- Zapier and Make.com connectors
- GraphQL API alongside REST
- Official client libraries (Python, JavaScript, Go)
- Mobile app for monitoring and basic management
- Plugin system for custom extensions
- Marketplace for community-contributed integrations

**Target Audience**: No-code users and developers seeking pre-built integrations.

---

## Architecture Philosophy

WARAS follows a layered architecture that separates concerns and enables flexibility:

**Client Layer**: Any HTTP or WebSocket client (automation tools, scripts, applications)

**API Gateway**: HTTP server providing REST endpoints, WebSocket handlers, authentication, and request validation

**Business Logic**: Session orchestration, message queuing, event dispatching, and state management

**WhatsApp Core**: Protocol implementation, encryption, WebSocket connection to WhatsApp servers, and media handling

**Storage Layer**: Pluggable backends for session persistence and message history

This separation allows each layer to evolve independently and makes it possible to swap implementations (e.g., SQLite to PostgreSQL) without affecting other components.

---

## Technical Foundations

### Why Rust?

Rust was chosen for WARAS based on specific technical requirements:

- **Memory Safety**: Eliminates entire classes of bugs common in C/C++ without runtime overhead
- **Performance**: Native compilation produces binaries comparable to C in speed
- **Concurrency**: Strong concurrency primitives make multi-session handling safe and efficient
- **Ecosystem**: Mature libraries for HTTP, WebSocket, cryptography, and async I/O
- **Binary Size**: Aggressive optimization produces small executables suitable for containerization

### Why API-First?

Traditional WhatsApp bot frameworks couple the bot logic with WhatsApp connection management. This creates deployment rigidity and forces developers to work within the framework's constraints.

WARAS inverts this model: it handles only WhatsApp protocol concerns and exposes all functionality through an API. This means:

- Your application logic runs separately and can be written in any language
- Updating your bot logic does not require restarting WhatsApp sessions
- Multiple applications can share the same WhatsApp sessions
- Testing becomes simpler since you can mock the WARAS API

### Why Self-Hosted First?

WhatsApp accounts are personal and often tied to regulated use cases (customer support, healthcare, finance). Many organizations cannot legally send WhatsApp data to third-party SaaS providers.

By designing for self-hosting from day one, WARAS ensures these users have a viable solution while still allowing for a future managed option for those who prefer convenience over control.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

Based on [whatsapp-rust](https://github.com/jlucaso1/whatsapp-rust) by jlucaso1 (MIT License).

---

## Disclaimer

WARAS is an unofficial, reverse-engineered implementation of the WhatsApp Web protocol. It is not endorsed by or affiliated with Meta Platforms, Inc.

**Important Considerations**:

- Using unofficial WhatsApp clients may violate Meta's Terms of Service
- Accounts using unofficial clients risk suspension or permanent ban
- This software is provided as-is without warranty of any kind
- Users are responsible for compliance with applicable laws and regulations

**Recommended Use Cases**:

- Research and educational purposes
- Personal automation with non-critical accounts
- Self-hosted deployments with appropriate backup and contingency plans

**Not Recommended For**:

- Production systems without backup WhatsApp accounts
- Bulk messaging or spam
- Any use case that violates WhatsApp Terms of Service or applicable laws

---

## Acknowledgements

WARAS builds upon the work of several open-source projects and protocol implementations:

- **whatsapp-rust** - Base Rust implementation providing core protocol handling
- **whatsmeow** - Go implementation serving as protocol reference
- **Baileys** - TypeScript implementation providing protocol insights
- **Signal Protocol** - End-to-end encryption specification and implementation

---

## Contributing

Contributions are welcome and encouraged. Areas where contributions would be particularly valuable:

- Documentation improvements and examples
- Protocol analysis and reverse engineering
- Storage backend implementations
- Client library development
- Integration examples with popular automation tools

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting pull requests.

---

<div align="center">

Built with Rust

**[Back to Top](#waras---whatsapp-remote-automation-service)**

</div>
