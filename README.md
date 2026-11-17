# SupportOrderService

An internal system for managing support orders at an IT repair shop. It is designed to run inside a Docker container on a computer in the shop, and to be accessed by the company's workers over the local network.

## Tech Stack

- [.NET 10](https://dotnet.microsoft.com/)
- [Entity Framework Core](https://learn.microsoft.com/ef/core/)
- [MudBlazor](https://mudblazor.com/) for the UI components
- [PostgreSQL](https://www.postgresql.org/) as the database

## Getting Started

### Prerequisites

> [!IMPORTANT]
> Either **Docker Engine** or **Docker Desktop** is required to run this application.

- [Docker Engine](https://docs.docker.com/engine/install/) or [Docker Desktop](https://docs.docker.com/desktop/)
- Docker Compose (already included in Docker Desktop and recent Docker Engine installs)

### Installation

1. Clone the repository:

   ```shell
   git clone https://github.com/hortma/SupportOrderService.git
   cd SupportOrderService
   ```

2. Build and start the containers:

   ```shell
   docker compose up --build
   ```

3. Once the containers are running, open the application in your browser:

   ```
   http://localhost:8080
   ```

   Other computers on the local network can reach it at `http://<host-machine-ip>:8080`.
