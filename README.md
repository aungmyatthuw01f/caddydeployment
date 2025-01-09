# Caddy Reverse Proxy with Basic Authentication

This repository contains the Docker Compose configuration for deploying Caddy as a reverse proxy with basic authentication to secure the admin interface of a web application.

## Overview

The setup uses Caddy as the front-facing web server to handle HTTPS requests and to provide secure access to an admin area of a web application. The configuration details are specified in `docker-compose.yml` and `Caddyfile` files.

## Prerequisites

- Docker and Docker Compose installed on your system.
- Domain name with DNS configured to point to the server where you are deploying Caddy.

## Configuration Files

- `docker-compose.yml`: Defines the services, networks, and volumes.
- `Caddyfile`: Contains the Caddy configuration for reverse proxy settings and basic authentication.

## Setup Instructions

### Step 1: Clone the Repository

Clone this repository to your local machine or server:

```bash
git clone https://github.com/aungmyatthuw01f/caddydeployment.git
cd caddydeployment
```

### Step 2: Environment Setup

Create a `.env` file in the root of your project directory to store sensitive variables:

```plaintext
ADMIN_USER=admin
ADMIN_PASSWORD_HASH=your_bcrypt_hashed_password
```

Replace `your_bcrypt_hashed_password` with the BCrypt hash of your desired password.

### Step 3: Running Docker Compose

To start the services, run:

```bash
docker-compose up -d
```

This command will pull the required Docker images, create volumes, and start the services defined in `docker-compose.yml`.

### Step 4: Accessing the Web Application

Open a web browser and navigate to:

- `https://your-domain.com` - Main website accessible to the public.
- `https://your-domain.com/admin` - Admin interface protected by basic authentication.

### Step 5: Stopping the Services

To stop the running services, use:

```bash
docker-compose down
```

## Security Recommendations

- Always use HTTPS to secure your connections.
- Keep your Docker environment updated.
- Store sensitive information such as passwords securely using environment variables or Docker secrets.

## Troubleshooting

If you encounter issues with accessing the services, check the Docker and Caddy logs:

```bash
docker-compose logs caddy
```

For more detailed troubleshooting, consult the [Caddy documentation](https://caddyserver.com/docs/).

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
```