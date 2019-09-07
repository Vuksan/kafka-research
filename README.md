1. You will need `envsubst`. On macOS, install it with `brew`

`brew install gettext`
`brew link --force gettext`

1. You need to get your host IP and use it in `docker-compose.yml` (KAFKA_ADVERTISED_HOST_NAME). In my case on macOS my docker is on `en1`:

`host_ip=$(ipconfig getifaddr en1) envsubst < docker-compose.yml.template > docker-compose.yml`


1. producer.js and consumer.js must have $host_ip for `brokers`:

```
host_ip=$(ipconfig getifaddr en1) envsubst < producer.js.template > producer.js
host_ip=$(ipconfig getifaddr en1) envsubst < consumer.js.template > consumer.js
```


1. If you have older version of docker, you have to create `kafka` network first:

`docker network create kafka`


1. Run it:

`docker-compose up -d`
