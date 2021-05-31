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

mm-mysql:
    ...
    build:
        ...
        args:
            - ROOT_PASSWORD=root
            - DATABASE=mattermost
            - USER=mmuser
            - PASSWORD=mmpass
    ...

mm:
    ...
    build:
        ...
        args:
            ...
            - DATABASE=mattermost
            - DB_USER=mmuser
            - DB_PASSWORD=mmpass
    ...
```

### Optional docker build parameters

```yaml
# docker-compose.yml

mm:
    ...
    build:
        ...
        args:
            - MM_VER=5.35.1
            - DB_HOST=mm-mysql
            - DB_PORT=3306
    ...
```

### Run mattermost

```
docker-compose build
```
```
docker-compose up
```

Access to `http://localhost:8065`
