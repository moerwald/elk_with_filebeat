# elk_with_filebeat
Starts an ELK and a filebeat container. The filebeat container indexes files (suffix must be *.log) configured in the bind mount in the docker-compose.yml file. After starting the containers kibana is avaiable via http://localhost:5601.

# How to start
Update the volume in docker-compose.yml with your local drive where you want to index a bunch of log-files.

Switch to the directory where docker-compose.yml is located and start the containers via:

> docker-compose up

If you want to star the containers in a daemonized way you can use:

> docker-compose up -d

To gather the logfiles of the container perform:

> docker container ls

and call "log" on the container you wish to check. E.g.

> docker container log --tail -f elk_filebeat_1

#How to configure

## Filebeat container

Per default all files with suffix *.log are indexed. Location of the *.log files is configured in the docker-compose.yml file.

## ELK container

Adapt Dockerfile to copy several logstash filters to the docker image.
