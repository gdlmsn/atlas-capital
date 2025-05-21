# Trading Platform

A comprehensive trading platform that connects to multiple broker APIs (Interactive Brokers, TastyTrade, TradeStation), featuring trade journaling, planning tools, portfolio management, and AI-powered analytics.

## Overview

This platform allows traders to:

- Connect to multiple broker accounts from a single interface
- Track positions, orders, and trades across all connected brokers
- Maintain a structured trade journal with analytics
- Plan trades with risk management tools
- Access AI-powered insights and analytics
- View consolidated portfolio data

## Project Structure

This project is organized as a monorepo to facilitate code sharing between web and mobile applications:

```
trading-platform-monorepo/
├── apps/                         # Applications
│   ├── web/                      # Next.js web application
│   ├── mobile/                   # React Native mobile application
│   └── api/                      # Optional standalone API service
├── packages/                     # Shared packages
│   ├── core/                     # Business logic, services, and types
│   ├── database/                 # Database access and schema
│   ├── ui/                       # Shared UI components (if applicable)
│   ├── test-config/              # Testing configuration
│   └── storybook-config/         # Storybook configuration
└── e2e-tests/                    # End-to-end tests
```

### Web Application

The web application is built with Next.js, providing a responsive interface for desktop and mobile browsers:

- **Authentication** - Secure login with email and OAuth providers
- **Dashboard** - Overview of portfolio performance and key metrics
- **Portfolio** - Consolidated view of positions across all brokers
- **Trade Journal** - Detailed trade logging and analysis
- **Trade Planner** - Tools for planning and risk management
- **AI Assistant** - AI-powered insights and analytics

### Mobile Application

The React Native mobile application shares core business logic with the web app while providing a native mobile experience:

- **Core features** - Access to the same data and functionality as the web app
- **Native UI** - Optimized for touch interfaces and mobile screens
- **Offline capabilities** - Basic functionality when internet connection is limited

### Shared Packages

The `packages/` directory contains shared code used by both applications:

- **core** - Services for broker integrations, AI analysis, and shared business logic
- **database** - Database schema and access layer using Drizzle ORM
- **ui** - Shared UI components where applicable
- **test-config** - Centralized Jest configuration
- **storybook-config** - Centralized Storybook configuration

## Technology Stack

### Frontend

- **Next.js** - React framework with App Router
- **React Native** - For mobile application
- **TailwindCSS** - Utility-first CSS framework
- **shadcn/ui** - High-quality UI components
- **TanStack Query** - Data fetching and caching
- **Zustand** - State management
- **TradingView** - Charts integration

### Backend

- **Next.js API Routes** - API endpoints for web app
- **Neon PostgreSQL** - Serverless PostgreSQL database
- **Drizzle ORM** - Type-safe database access
- **NextAuth.js** - Authentication system

### DevOps

- **pnpm Workspaces** - Package management
- **GitHub Actions** - CI/CD automation
- **Jest** - Unit and integration testing
- **Playwright** - End-to-end testing
- **Docker** - Containerization

### AI Integration

- **OpenAI API** - For AI-powered analytics
- **Claude API** - For conversational assistant

## Getting Started

### Prerequisites

- Node.js 18+
- pnpm 8+
- Docker (optional, for local development services)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/trading-platform.git
   cd trading-platform
   ```

2. Install dependencies:

   ```bash
   pnpm install
   ```

3. Set up environment variables:

   ```bash
   cp apps/web/.env.example apps/web/.env.local
   # Edit .env.local with your configuration
   ```

4. Start the development server:

   ```bash
   # Start the web application
   pnpm dev:web

   # Start the mobile application (when available)
   pnpm dev:mobile
   ```

### Database Setup

1. Create a Neon PostgreSQL database (or use Docker):

   ```bash
   # If using Docker for local development
   docker-compose up -d postgres
   ```

2. Run migrations:
   ```bash
   pnpm db:migrate
   ```

## Development Workflow

### Web Development

```bash
# Start Next.js dev server
pnpm dev:web

# Run tests
pnpm test:web

# Start Storybook
pnpm storybook:web
```

### Mobile Development

```bash
# Start Expo dev server
pnpm dev:mobile

# Run tests
pnpm test:mobile
```

### Testing

```bash
# Run all tests
pnpm test

# Run end-to-end tests
pnpm test:e2e
```

## Broker Integration

The platform currently supports or plans to support the following brokers:

- **Interactive Brokers** - Uses the Client Portal API
- **TastyTrade** - Planned future integration
- **TradeStation** - Planned future integration

Each broker integration is implemented as a service in the core package, with a consistent adapter pattern to normalize data across different brokers.

## AI Features

The platform incorporates AI capabilities including:

- **Trade Analysis** - AI-powered insights into trade patterns and performance
- **Market Research** - Automated analysis of market conditions and securities
- **Assistant** - Conversational AI for answering trading-related questions
- **Journal Enhancement** - AI suggestions for improving trade journal entries

## Deployment

The platform can be deployed to various environments:

### Web Application

- Vercel (recommended for Next.js)
- AWS Amplify
- Cloudflare Pages
- Railway

### API (if separated)

- Railway
- AWS Lambda
- Digital Ocean

### Database

- Neon (serverless PostgreSQL)
- Supabase
- AWS RDS

## Contributing

Contributions are welcome! Please check out our [Contributing Guide](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
