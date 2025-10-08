# PhnxHTMX 🔥

> Phoenix meets HTMX: Hypermedia-driven web development with Elixir's concurrency and fault tolerance. Because not every interaction needs a JavaScript framework.

A Phoenix 1.7 web application showcasing hypermedia-driven architecture with HTMX, LiveView components, and Elixir's powerful OTP primitives. Demonstrates how functional programming, actor-based concurrency, and server-side rendering can deliver rich user experiences without heavy client-side JavaScript.

## Overview

PhnxHTMX explores the intersection of Phoenix's real-time capabilities and HTMX's hypermedia approach. Built on Elixir/OTP, it leverages the BEAM VM's lightweight processes and fault tolerance while delivering interactive UIs through progressive enhancement rather than single-page application complexity.

## Skills Demonstrated

This project showcases Elixir/Phoenix web development with modern patterns:

- **Phoenix Framework Expertise**: Phoenix 1.7 with function components, HEEx templates, Ecto for database interactions, Plug middleware pipeline, and Phoenix.HTML for server-rendered markup. Demonstrates idiomatic Phoenix patterns including controller actions, HTML view modules, and component composition.

- **Hypermedia-Driven Architecture**: HTMX integration for dynamic interactions without JavaScript frameworks. Server returns HTML fragments that progressively enhance the user experience, demonstrating REST-first architecture where hypermedia is the engine of application state (HATEOAS).

- **Phoenix LiveView**: Real-time server-rendered components using WebSocket connections for stateful interactions. Showcases how LiveView's diff-based updates enable real-time UIs with minimal client-side code while maintaining server-side state management.

- **Elixir/OTP Patterns**: Functional programming with pattern matching, supervision trees via Application behavior, GenServer processes for stateful components, and BEAM VM's preemptive scheduling for concurrent request handling demonstrating the actor model in production.

- **Internationalization (i18n)**: Gettext integration for multi-language support with message extraction, translation catalogs, and runtime locale switching via custom Plug middleware supporting English, French, German, and Spanish.

- **Database Integration**: Ecto ORM with SQLite (ecto_sqlite3) for embedded database, migration workflows, schema definitions, and composable query patterns demonstrating Elixir's approach to data modeling and persistence.

- **Asset Pipeline**: Modern asset handling with esbuild for JavaScript bundling and TailwindCSS for utility-first styling with JIT compilation. Mix tasks for asset setup, building, and deployment demonstrate Phoenix's integrated toolchain.

- **Testing & Quality**: ExUnit test framework with Phoenix-specific test helpers, Floki for HTML parsing in tests, and Mix tasks for continuous integration demonstrating TDD patterns in Elixir.

- **Observability**: Telemetry for metrics collection, Phoenix.LiveDashboard for real-time application monitoring, Telemetry.Metrics for measurement, and Telemetry.Poller for periodic collection showing production-ready monitoring.

- **Email Integration**: Swoosh for composable email with multiple adapters, demonstrating how Phoenix handles background tasks and external service integration through OTP behaviors.

## Tech Stack

### Core Framework
- **Elixir** ~> 1.14 - Functional language on the BEAM VM
- **Phoenix** ~> 1.7.10 - Web framework with real-time capabilities
- **Phoenix.LiveView** ~> 0.20.1 - Real-time server-rendered components

### Database & ORM
- **Ecto** ~> 3.10 - Database wrapper and language integrated query
- **Ecto.SQL** - SQL adapter for Ecto
- **ecto_sqlite3** - SQLite3 adapter for Ecto

### Frontend & Interactivity
- **HTMX** - Hypermedia-driven interactions (via CDN)
- **Phoenix.HTML** ~> 3.3 - HTML helper functions
- **Phoenix.LiveReload** ~> 1.2 - Hot reload in development
- **TailwindCSS** ~> 0.2.0 - Utility-first CSS framework
- **esbuild** ~> 0.8 - JavaScript bundler

### Internationalization
- **Gettext** ~> 0.20 - Internationalization and localization
- **Custom Locale Plug** - Request-based locale switching

### Observability & Monitoring
- **Phoenix.LiveDashboard** ~> 0.8.2 - Real-time metrics dashboard
- **Telemetry.Metrics** ~> 0.6 - Metric definitions
- **Telemetry.Poller** ~> 1.0 - Periodic metric collection

### Infrastructure
- **Plug.Cowboy** ~> 2.5 - HTTP server adapter
- **Swoosh** ~> 1.3 - Email composition and delivery
- **Finch** ~> 0.13 - HTTP client for external APIs
- **DNS Cluster** ~> 0.1.1 - DNS-based cluster formation
- **Jason** ~> 1.2 - JSON encoding/decoding

### Development & Testing
- **Phoenix.LiveReload** - Asset hot-reloading
- **Floki** >= 0.30.0 - HTML parsing for tests
- **ExUnit** - Built-in testing framework

## Project Structure

```
phnxhtmx/
├── lib/
│   ├── phnxhtmx/
│   │   ├── application.ex      # OTP application startup
│   │   ├── repo.ex             # Ecto repository
│   │   └── mailer.ex           # Email configuration
│   └── phnxhtmx_web/
│       ├── controllers/        # HTTP controllers
│       │   ├── page_controller.ex
│       │   ├── page_html.ex
│       │   ├── todo_controller.ex
│       │   └── todo_html.ex
│       ├── components/         # Reusable components
│       │   ├── core_components.ex
│       │   └── layouts.ex
│       ├── plugs/              # Custom middleware
│       │   └── locale.ex       # i18n locale detection
│       ├── endpoint.ex         # HTTP endpoint
│       ├── router.ex           # Route definitions
│       ├── gettext.ex          # i18n configuration
│       └── telemetry.ex        # Metrics definitions
├── priv/
│   ├── repo/
│   │   ├── migrations/         # Database migrations
│   │   └── seeds.exs           # Seed data
│   ├── static/                 # Static assets
│   └── gettext/                # Translation files
├── assets/
│   ├── css/                    # Stylesheets
│   ├── js/                     # JavaScript
│   └── vendor/                 # Third-party assets
├── test/                       # Test files
├── config/                     # Application configuration
└── mix.exs                     # Project definition
```

## Getting Started

### Prerequisites
- Elixir >= 1.14
- Erlang/OTP >= 25
- Node.js >= 18 (for asset building)

### Installation

```bash
# Clone the repository
git clone https://github.com/ashmortar/phnxhtmx.git
cd phnxhtmx

# Install dependencies, create database, and build assets
mix setup
```

### Development

```bash
# Start Phoenix server
mix phx.server

# Or run inside IEx for interactive debugging
iex -S mix phx.server

# Run tests
mix test

# Run tests in watch mode
mix test.watch
```

Visit http://localhost:4000 to see the application.

### Database Management

```bash
# Create database
mix ecto.create

# Run migrations
mix ecto.migrate

# Rollback migration
mix ecto.rollback

# Reset database (drop, create, migrate, seed)
mix ecto.reset

# Run seeds
mix run priv/repo/seeds.exs
```

### Asset Management

```bash
# Install asset build tools
mix assets.setup

# Build assets
mix assets.build

# Build and minify for production
mix assets.deploy
```

### Building for Production

```bash
# Build release
MIX_ENV=prod mix release

# Run release
_build/prod/rel/phnxhtmx/bin/phnxhtmx start
```

## Architecture Highlights

### HTMX Integration

Server returns HTML fragments for dynamic updates:

```elixir
# Controller returns partial HTML
def show(conn, %{"id" => id}) do
  conn
  |> put_layout(false)  # Skip layout for HTMX request
  |> render(:show, id: id)
end
```

```heex
<!-- Template with HTMX attributes -->
<div hx-get={~p"/todos/#{@id}"} hx-trigger="click">
  Load todo details
</div>
```

### Phoenix LiveView

Real-time components with minimal JavaScript:

```elixir
defmodule PhnxhtmxWeb.DashboardLive do
  use PhnxhtmxWeb, :live_view

  def mount(_params, _session, socket) do
    if connected?(socket) do
      # Subscribe to real-time updates
      Phoenix.PubSub.subscribe(Phnxhtmx.PubSub, "todos")
    end
    {:ok, assign(socket, todos: load_todos())}
  end

  def handle_info({:todo_updated, todo}, socket) do
    {:noreply, update(socket, :todos, &update_todo(&1, todo))}
  end
end
```

### Internationalization

Custom Plug for locale detection:

```elixir
defmodule PhnxhtmxWeb.Plugs.Locale do
  import Plug.Conn

  @locales ["en", "fr", "de", "es"]

  def call(%Plug.Conn{params: %{"locale" => locale}} = conn, _default)
      when locale in @locales do
    assign(conn, :locale, locale)
  end

  def call(conn, default) do
    assign(conn, :locale, default)
  end
end
```

### OTP Application Structure

Supervision tree managing application processes:

```elixir
defmodule Phnxhtmx.Application do
  use Application

  def start(_type, _args) do
    children = [
      PhnxhtmxWeb.Telemetry,
      Phnxhtmx.Repo,
      {DNSCluster, query: Application.get_env(:phnxhtmx, :dns_cluster_query) || :ignore},
      {Phoenix.PubSub, name: Phnxhtmx.PubSub},
      {Finch, name: Phnxhtmx.Finch},
      PhnxhtmxWeb.Endpoint
    ]

    Supervisor.start_link(children, strategy: :one_for_one)
  end
end
```

## Deployment

### Production Configuration

Set required environment variables:

```bash
export SECRET_KEY_BASE=$(mix phx.gen.secret)
export DATABASE_PATH=/app/data/phnxhtmx.db
export PHX_HOST=example.com
export PORT=4000
```

### Deployment Options

Phoenix apps can be deployed to:
- **Fly.io** - Excellent Elixir/Phoenix support with clustering
- **Gigalixir** - Elixir-specific platform
- **Heroku** - With Elixir buildpack
- **Docker** - Via mix release in container
- **Traditional VPS** - Systemd service with mix release

See [Phoenix deployment guides](https://hexdocs.pm/phoenix/deployment.html) for details.

## Why Phoenix + HTMX?

This architecture combines:

- **Phoenix's strengths**: Real-time capabilities, fault tolerance, low latency
- **HTMX's simplicity**: Progressive enhancement, minimal JavaScript, HTML over-the-wire
- **Elixir/OTP benefits**: Actor model concurrency, immutable data, pattern matching

The result: Rich interactive experiences with minimal client complexity, leveraging decades of battle-tested BEAM VM reliability.

## Contributing

Personal project exploring hypermedia-driven patterns in Elixir. Feedback welcome via issues.

## License

UNLICENSED - Personal exploration project.

---

**Author:** [Aaron Ross](https://github.com/ashmortar)

*Part of a curated collection investigating how different technologies approach similar problems. This project explores whether Phoenix's real-time capabilities and Elixir's concurrency model can deliver the responsiveness users expect from SPAs while maintaining the simplicity and reliability of hypermedia-driven architectures. The hypothesis: HTMX + LiveView might be the sweet spot between developer experience and operational simplicity.*
