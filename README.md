# Websphere Docker w/ Elk Stack Logging

Test application that logs to a dockerised ELK stack. Uses:
- log4j output in JSON format
- Docker log-driver mechanism (via syslog) to update logstash

## Splunk Stack

1. `docker pull splunk/splunk:latest`
2. `docker run -d -e SPLUNK_START_ARGS=--accept-license -e SPLUNK_USER=root -p 8000:8000 -p 8088:8088 splunk/splunk`

## Test App

1. Build war: `mvn install`
2. Build docker image: `docker build --tag web .`
3. Run web app: `docker-compose up -d`

## Verify

1. Open `http://localhost/websphere_elk_test`
2. Open `http://localhost:8000` and sign-in
3. Navigate to Search & Reporting
4. Click on the Data Summary button
5. Click on the `moby` link
6. Verify `This is a test message` has been captured
