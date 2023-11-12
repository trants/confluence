<p align="center">
	<img src="https://walruship-repository.s3.ap-southeast-1.amazonaws.com/images/confluence_logo.png" alt="Confluence-Logo">
</p>

This project comes as a pre-built docker image that enables you to easily installation Confluence without having to know too much about setup Confluence.

## Features
- Supports almost all plug-ins.
- Support DataCenter mode.
- Compared with traditional crack, you can easily upgrade your service without having to crack it again.
- Provides a java-based command line keygen, which is more convenient to use in a terminal environment.

## Quick Setup

1. Install Docker and Docker-Compose
- [Docker Install documentation](https://docs.docker.com/install/)
- [Docker-Compose Install documentation](https://docs.docker.com/compose/install/)

2. Bring up your stack by running
```shell
git clone https://github.com/trants/confluence.git \
    && cd confluence \
    && cp .env.example .env
```

3. Edit environment variable
```bash
# Confluence
ATL_PROXY_NAME=localhost
ATL_PROXY_PORT=443
ATL_TOMCAT_PORT=8090
ATL_TOMCAT_SCHEME=https
ATL_TOMCAT_SECURE=true
JVM_CODE_CACHE_ARGS="-XX:InitialCodeCacheSize=1g -XX:ReservedCodeCacheSize=8g"
JVM_MAXIMUM_MEMORY=12g
JVM_MINIMUM_MEMORY=1g
TZ=UTC
PORT=8090

# MySQL
MYSQL_DATABASE=database
MYSQL_PASSWORD=password
MYSQL_ROOT_PASSWORD=rootpassword
MYSQL_USER=user

# Backup
SCHEDULE=@weekly
BACKUP_KEEP_DAYS=7
S3_ACCESS_KEY_ID=AKIA3M3ZKBJPQUBT2UK6
S3_BUCKET=my-s3-bucket
S3_PREFIX=prefix
S3_REGION=us-east-1
S3_SECRET_ACCESS_KEY=BNcXdm18XMctzMH87PZLm8UoP6WlegcPvsQbF5TH
MYSQL_DATABASE=database
MYSQL_HOST=mysql
MYSQL_PASSWORD=password
MYSQL_USER=user
PASSPHRASE=wxHw26GJZQBDenA8
```
4. Start confluence
```shell
docker-compose up -d
```

## How to hack Confluence
```shell
docker exec confluence java -jar /var/agent/atlassian-agent.jar \
    -d \
    -p conf \
    -m email@example.com \
    -n email@example.com \
    -o http://yourdomain.com \
    -s you-server-id-xxxx
```

## How to hack confluence plugin
- Example I want to use BigGantt plugin
1. Install BigGantt from confluence marketplace.
2. Find `App Key` of BigGantt is : `eu.softwareplant.biggantt`
3. Execute :
```shell
docker exec confluence java -jar /var/agent/atlassian-agent.jar \
    -d \
    -p eu.softwareplant.biggantt \
    -m email@example.com \
    -n email@example.com \
    -o http://yourdomain.com \
    -s you-server-id-xxxx
```
4. Paste your license


## How to upgrade

```shell
cd confluence && git pull
docker pull trants/confluence:latest && docker-compose stop
docker-compose rm
```

## Security
- If you discover any security related issues, please email 286.trants@gmail.com instead of using the issue tracker.

## License
- This software is released under the [BSD 3-Clause][link-license] License. Please see the [LICENSE](LICENSE) file or https://walruship.com/LICENSE.txt for more information.

[link-license]: https://opensource.org/license/bsd-3-clause/