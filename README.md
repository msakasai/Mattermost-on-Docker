# Mattermost-on-Docker

## Usage

### Create docker network

```bash
docker network ls

docker network create mattermost

docker network ls
```

### Editing docker-compose.yml

- Mysql root password
- Mysql mmuser password

ex.
```yaml
# docker-compose.yml

environment:
    MYSQL_ROOT_PASSWORD: root
    MYSQL_DATABASE: mattermost
    MYSQL_USER: mmuser
    MYSQL_PASSWORD: mmpass
```

### Optional docker build parameters

```yaml
# docker-compose.yml

build:
    context: mattermost/
    dockerfile: Dockerfile
    args:
        - MM_VER=5.35.1 # mattermost version
        - DB_HOST=mm-mysql # mysql hostname
        - DB_PORT=3306 # mysql port
```

### Run mattermost

```
docker-compose build
```
```
docker-compose up
```

Access to `http://localhost:8065`
