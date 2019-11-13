# translatome-workbench

# Introduce
Translatome workbench is a web server for translatome related analysis,which can be accessed online by visiting our public website or deployed to personal computer by a docker image.The workbench is based on the Galaxy framework which integrates common tools for translatomics.
# Installation and Setup:
## Requirements:
The only requirement to run this webserver locally is [Docker](https://docs.docker.com/installation).Docker supports the three major desktop operating systems Linux, Windows and Mac OSX. Please refer to Docker installation [guideline](https://docs.docker.com/installation) for details.
## Running the Galaxy server:
### From the command line (Linux/Windows/MacOS):
#### Pull image:
    docker run -it -p 8080:8080 -p 2880:80 registry.eu-west-1.aliyuncs.com/sysuzoc/translatome:1.0
#### Start related service:
    service apache2 start
    service influxdb start
    service grafana-server start
    service telegraf start
    /etc/init.d/postgresql start
Command postgresql and influxdb may return failed,rerun command for postgresql and ignore influxdb. 
#### Setup job monitor on galaxy welcome page:
    su - galaxy
    vim /home/galaxy/galaxy/static
Find "iframe" element and set your IP.
#### Start server:
    sh /home/galaxy/galaxy/run.sh
### Browser access to the server:
    http://YOURIP:8080

