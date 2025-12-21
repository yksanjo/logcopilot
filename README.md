# LogCopilot - Log Intelligence Platform

<div align="center">

![LogCopilot Logo](https://via.placeholder.com/200x200/22c55e/ffffff?text=LogCopilot)

**AI-Powered Log Analysis for Non-Security Experts**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.3-blue.svg)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-14-black.svg)](https://nextjs.org/)

[Features](#-features) • [Quick Start](#-quick-start) • [Screenshots](#-screenshots) • [API Docs](#-api-documentation) • [Pricing](#-pricing)

</div>

---

## 🎯 Overview

**LogCopilot** makes log analysis accessible to everyone. With natural language queries and AI-powered anomaly detection, you don't need to be a security expert to understand what's happening in your systems.

### Why LogCopilot?

- 🗣️ **Natural Language** - Ask questions in plain English
- 🤖 **AI-Powered** - Automatic anomaly detection with explanations
- 📊 **Multi-Source** - Ingest from API, S3, OpenTelemetry, webhooks
- 🎯 **Actionable** - Get playbook suggestions, not just alerts
- 💰 **Affordable** - $49-149/month, perfect for SMBs

## ✨ Features

### Core Capabilities

- **Natural Language Log Analysis**
  - Ask questions like "What errors happened in the last hour?"
  - Get plain-English explanations of log patterns
  - No need to learn query languages

- **AI Anomaly Detection**
  - Automatically detects unusual patterns
  - Explains why something is suspicious
  - Provides severity ratings

- **Multi-Source Ingestion**
  - REST API endpoints
  - S3 bucket monitoring
  - OpenTelemetry integration
  - Webhook support

- **Actionable Playbooks**
  - Step-by-step remediation guides
  - Slack/email notifications
  - Integration with incident response tools

## 🚀 Quick Start

### Prerequisites

- Node.js 20+ and npm
- PostgreSQL 15+ (or Docker)
- OpenAI API Key

### Installation

```bash
# Clone the repository
git clone https://github.com/yksanjo/logcopilot.git
cd logcopilot

# Install dependencies
cd backend && npm install
cd ../frontend && npm install

# Set up environment variables
cp backend/.env.example backend/.env
# Edit backend/.env with your configuration

# Start database (using Docker)
docker-compose up -d postgres

# Run migrations
cd backend && npm run migrate

# Start development servers
cd backend && npm run dev  # Terminal 1
cd frontend && npm run dev # Terminal 2
```

### Docker Compose (Recommended)

```bash
docker-compose up -d
```

Access the application at http://localhost:3000

## 📸 Screenshots

### Dashboard Overview

![Dashboard](screenshots/dashboard.png)

*Unified view of all log sources and anomalies*

### Log Sources

![Sources](screenshots/sources.png)

*Configure and manage multiple log sources*

### Anomaly Detection

![Anomalies](screenshots/anomalies.png)

*AI-detected anomalies with plain-English explanations*

### Natural Language Queries

![Queries](screenshots/queries.png)

*Ask questions in plain English*

> **Note:** Screenshots are located in the `/screenshots` directory. See [SCREENSHOTS.md](screenshots/README.md) for details.

## 🏗️ Architecture

```
logcopilot/
├── backend/                 # Express.js API
│   ├── src/
│   │   ├── routes/         # API endpoints
│   │   ├── services/       # Business logic
│   │   │   └── ai/         # OpenAI integration
│   │   └── db/             # Database migrations
│   └── package.json
├── frontend/               # Next.js application
│   ├── app/               # App router pages
│   ├── components/        # React components
│   └── package.json
├── docker-compose.yml     # Docker setup
└── README.md
```

## 📚 API Documentation

### Authentication

All endpoints require authentication via JWT token:

```bash
Authorization: Bearer <your-token>
x-organization-id: <org-id>
```

### Endpoints

#### Log Sources

```bash
# List log sources
GET /api/logs/sources

# Add log source
POST /api/logs/sources
{
  "name": "Production Logs",
  "source_type": "api",
  "config": { ... }
}
```

#### Log Ingestion

```bash
# Ingest logs
POST /api/logs/ingest
{
  "source_id": "...",
  "logs": [...]
}
```

#### Anomalies

```bash
# List anomalies
GET /api/logs/anomalies?severity=high

# Update anomaly status
PATCH /api/logs/anomalies/:id
{
  "status": "resolved"
}
```

## 💰 Pricing

| Plan | Price | Features |
|------|-------|----------|
| **Starter** | $49/month | Up to 1M logs/month, basic analysis |
| **Professional** | $99/month | Up to 10M logs/month, AI analysis, playbooks |
| **Enterprise** | $149/month | Unlimited logs, custom integrations, SLA |

14-day free trial • No credit card required

## 🛣️ Roadmap

- [ ] Natural language query interface
- [ ] Real-time log streaming
- [ ] Custom alert rules
- [ ] Integration with PagerDuty, Opsgenie
- [ ] Log retention policies
- [ ] Compliance reporting

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

<div align="center">

**Made with ❤️ for teams who want security without complexity**

[Get Started](#-quick-start) • [View Screenshots](#-screenshots) • [Read Docs](docs/)

</div>

