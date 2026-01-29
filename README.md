# Charitize – Charity Organization Website Template

A Bootstrap 5 charity organization website template, containerized with Docker for easy deployment.

## Docker Deployment

This project is configured to run with Docker using nginx web server.

### Build Docker Image
```bash
docker build -t img-html .
```

### Run Docker Container
```bash
docker run -d -p 8080:80 --name con-html img-html
```

### Access Application
Open your browser and navigate to: `http://localhost:8080`

### Stop Container
```bash
docker stop con-html
```

### Remove Container
```bash
docker rm con-html
```

## Credits

- **Template**: [HTML Codex](https://htmlcodex.com/)
- **License**: MIT
- **Distributed by**: [ThemeWagon](https://themewagon.com)