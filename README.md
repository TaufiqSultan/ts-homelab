# TS-Homelab

Welcome to the **TS-Homelab** repository. This project serves as a centralized collection of Docker-based configurations for self-hosted services and applications. It is designed to simplify the deployment and management of a personal homelab environment.

## 📂 Repository Structure

The repository is organized by service. Each directory represents a standalone service or a stack of related services containing its own deployment configuration.

```
ts-homelab/
├── [service-name]/
│   ├── docker-compose.yml   # Docker composition for the specific service
│   └── .env.example         # Template for environment variables
├── .gitignore
└── README.md
```

## ☁️ Deployment Strategy: GitOps & Portainer

This homelab utilizes a **GitOps** approach powered by **Portainer**.

- **Single Source of Truth**: This GitHub repository serves as the definitive source for all service configurations.
- **Portainer Stacks**: Services are deployed as "Stacks" within Portainer, configured to pull directly from this repository (Repository > Auto-update).
- **Continuous Deployment**: Portainer is set to poll this repository. Merging changes to the `main` branch automatically triggers Portainer to pull the latest `docker-compose.yml` and redeploy the affected stacks.

_Note: The environment variables (`.env`) must be manually configured within Portainer's "Environment variables" section for each stack, as they are not stored in the repo._

## 🚀 Manual / Local Deployment

Use the following method for testing services locally (outside of Portainer) or for manual debugging.

### Prerequisites

Ensure you have the following installed on your host machine:

- [Docker Engine](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/downloads)

### Deployment Workflow

To deploy a new service, follow this standard workflow:

1.  **Clone the Repository**

    ```bash
    git clone https://github.com/TaufiqSultan/ts-homelab.git
    cd ts-homelab
    ```

2.  **Navigate to the Service Directory**
    Choose the service you want to deploy.

    ```bash
    cd [service-name]
    ```

3.  **Configure the Environment**
    Create your local environment file from the example template. This file contains sensitive configuration (API keys, passwords, paths) and is excluded from version control.

    ```bash
    cp .env.example .env
    ```

    _Edit the `.env` file with your specific preferences and secure values using your preferred text editor (e.g., `nano` or `vim`)._

4.  **Launch the Service**
    Start the service in detached mode:
    ```bash
    docker-compose up -d
    ```

## 🛠️ Maintenance

### Updating a Service

To update a specific service to the latest image versions defined in your compose file:

```bash
cd [service-name]
docker-compose pull
docker-compose up -d
```

### Stopping a Service

To stop and remove the containers for a specific service:

```bash
cd [service-name]
docker-compose down
```

## 📄 License

This project is for personal use and documentation. Please refer to the individual software licenses for the specific services contained within this repository.
