1. You will need `envsubst`. On macOS, install it with `brew`

`brew install gettext`
`brew link --force gettext`

2. You need to get your host IP and use it in `docker-compose.yml` (KAFKA_ADVERTISED_HOST_NAME). In my case on macOS my docker is on `en1`:

`host_ip=$(ipconfig getifaddr en1) envsubst < docker-compose.yml.template > docker-compose.yml`


3. producer.js and consumer.js must have $host_ip for `brokers`:

```
host_ip=$(ipconfig getifaddr en1) envsubst < producer.js.template > producer.js
host_ip=$(ipconfig getifaddr en1) envsubst < consumer.js.template > consumer.js
```


4. If you have older version of docker, you have to create `kafka` network first:

`docker network create kafka`


5. Run it:

`docker-compose up -d`

6. Get logs from container

..* Get the list of all running containers with `docker-compose ps`
..* Get logs from single container: `docker-compose logs -f CONTAINER_NAME`
..* Get logs from single all of them: `docker-compose logs -f`
