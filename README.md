# Introduction
This project leverages Docker Compose for container management and uses Infrastructure as Code (IaC) for automated infrastructure deployment.

# Set .env file
```env
# DB
MYSQL_ROOT_PASSWORD=
MYSQL_DATABASE=
MYSQL_USER=
MYSQL_PASSWORD=

# minIO
MINIO_ACCESS_KEY=
MINIO_SECRET_KEY=

# jupyter
JUPYTER_PASSWORD=

# vscode
VSCODE_YYLUI_PASSWORD=
VSCODE_CHIEH_PASSWORD=
VSCODE_QIAO_PASSWORD=
```

# Start Docker Compose services
```bash
docker-compose -f {fileName} up -d
```

# Stop Docker Compose service
```bash
docker-compose f {fileName} down
```

# Gitlab
https://medium.com/@a5822358/gitlab-72a1b32b5b5b