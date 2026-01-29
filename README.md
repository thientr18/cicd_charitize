# Charitize – Charity Organization Website Template

A Bootstrap 5 charity organization website template with **automated CI/CD deployment** to VPS using GitHub Actions and Docker.

## 🚀 CI/CD Deployment

This project features **automatic deployment** to VPS server whenever code is pushed to the `main` branch.

### Prerequisites
- VPS server with Docker installed
- GitHub repository secrets configured:
  - `VPS_IP`: Your VPS IP address
  - `VPS_KEY`: SSH private key for authentication
- GitHub repository variables:
  - `VPS_USER`: SSH username (e.g., root)

### Deployment Workflow

The CI/CD pipeline automatically:
1. ✅ Connects to VPS via SSH
2. ✅ Pulls latest code from GitHub
3. ✅ Rebuilds Docker containers
4. ✅ Deploys updated application
5. ✅ Cleans up unused Docker images

**Trigger deployment:**
- Push to `main` branch (automatic)
- Manual trigger via GitHub Actions UI

### VPS Server Setup

```bash
# 1. Clone repository on VPS
cd /root
git clone https://github.com/YOUR_USERNAME/cicd_charitize.git
cd cicd_charitize

# 2. Install Docker Compose V2
sudo apt update
sudo curl -L "https://github.com/docker/compose/releases/download/v2.24.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

# 3. Initial deployment
docker compose up -d --build
```

### Access Application
After deployment, access your site at: `http://YOUR_VPS_IP:8080`

## 🐳 Local Docker Development

### Using Docker Compose (Recommended)
```bash
# Start application
docker compose up -d --build

# Stop application
docker compose down
```

### Using Docker Commands
```bash
# Build image
docker build -t img-html .

# Run container
docker run -d -p 8080:80 --name con-html img-html

# Stop and remove
docker stop con-html && docker rm con-html
```

### Access Locally
Open browser: `http://localhost:8080`

## 📁 Project Structure

```
cicd_charitize/
├── .github/
│   └── workflows/
│       └── main.yaml          # CI/CD workflow configuration
├── Dockerfile                 # Docker image definition
├── docker-compose.yml         # Docker Compose configuration
└── [website files]            # HTML/CSS/JS files
```

## 🔧 Configuration Files

### GitHub Actions Workflow (`.github/workflows/main.yaml`)
- Automates SSH deployment to VPS
- Pulls code, rebuilds, and restarts containers
- Runs on push to `main` or manual trigger

### Docker Compose (`docker-compose.yml`)
- Service: nginx web server
- Port: 8080:80
- Auto-restart enabled

## 📝 Credits

- **Template**: [HTML Codex](https://htmlcodex.com/)
- **License**: MIT
- **Distributed by**: [ThemeWagon](https://themewagon.com)

## 🛠️ Troubleshooting

**Deployment fails?**
- Verify GitHub secrets are set correctly
- Check VPS has Docker Compose installed: `docker compose version`
- Ensure port 8080 is open on VPS firewall

**Container not starting?**
- Check logs: `docker compose logs`
- Verify Docker service: `sudo systemctl status docker`