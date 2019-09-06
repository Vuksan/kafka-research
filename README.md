# kafka-research

- Install dependencies:
```
yarn install
````

- Configure kafka:
```
docker-compose up -d
```

- Run producer with:
```
node producer.js
```

- Run consumer with:
```
node consumer.js
```

Enjoy!

# F.A.Q.
### 1. It doesn't work?  
Run the following command to get the IP of your host machine:
```
ifconfig | grep -E "([0-9]{1,3}\.){3}[0-9]{1,3}" | grep -v 127.0.0.1 | awk '{ print $2 }' | cut -f2 -d: | head -n1
```
In `docker-compose.yml` replace `KAFKA_ADVERTISED_HOST_NAME` value with your IP address.  
Change the IP adddress in `brokers` array of both `producer.js` and `consumer.js` to your IP. 
