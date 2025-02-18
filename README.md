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
## backup
### secret and rb (only change)
```bash
cp /etc/gitlab/gitlab-secrets.json /mnt/gitlab/
cp /etc/gitlab/gitlab.rb /mnt/gitlab/
```
### data
```bash
gitlab-rake gitlab:backup:create
cp /var/opt/gitlab/backups/{file} /mnt/gitlab/
```
## recovery
### rb (only change)
```bash
cp /mnt/gitlab/gitlab.rb /etc/gitlab/gitlab.rb
gitlab-ctl reconfigure
```
### data
```bash
# stop the service
gitlab-ctl stop puma
gitlab-ctl stop sidekiq

# copy the backup files
cp /mnt/gitlab/gitlab-secrets.json /etc/gitlab/gitlab-secrets.json
cp /mnt/gitlab/{file} /var/opt/gitlab/backups/
chown git.git /var/opt/gitlab/backups/{file}

# recovery the data
gitlab-rake gitlab:backup:restore

# restart the service
gitlab-ctl restart
```
