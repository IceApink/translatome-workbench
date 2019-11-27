# Galaxy-translatome-workbench

# Introduce
Translatome workbench is a web server for translatome related analysis,which can be accessed online by visiting our public website or deployed to personal computer by a docker image.The workbench is based on the Galaxy framework which integrates common tools for translatomics.
# Installation and Setup:
## Requirements:
The only requirement to run this webserver locally is [Docker](https://docs.docker.com/installation).Docker supports the three major desktop operating systems Linux, Windows and Mac OSX. Please refer to Docker installation [guideline](https://docs.docker.com/installation) for details.
### Hardware:
The size of the docker image is approximately 34GB,so make sure you have enough hard disk space.
#### Recommand hardware:
    CPU:  4 cores
    RAM:  8GB
    Disk: 100GB
## Running the Galaxy server:
### From the command line (Linux/Windows/MacOS):
#### Pull image
##### Asia:
    docker pull registry.cn-hongkong.aliyuncs.com/sysuzoc/translatome:1.0
#### Run container:
    docker run -it -p 8080:8080 -p 2880:80 --name="translatome-workbench" registry.cn-hongkong.aliyuncs.com/sysuzoc/translatome:1.0
#### Start related service:
    service apache2 restart
    service influxdb restart        #For monitor(optional)
    service grafana-server restart  #For monitor(optional)
    service telegraf restart        #For monitor(optional)
    /etc/init.d/postgresql start
Command postgresql and influxdb may return failed,rerun command for postgresql and ignore influxdb. 
#### Setup job monitor on galaxy welcome page:(optional)
    su - galaxy
    vim /home/galaxy/galaxy/static/welcome.html  #For monitor(optional)
    :/<iframe>                                   #For monitor(optional)
Find "<iframe>" element and set your IP.
#### Start server:
    sh /home/galaxy/galaxy/run.sh
#### Run backend:
    cd /home/galaxy/galaxy && 
    nohup sh run.sh > galaxy.log 2>&1 &
#### User and password
    galaxy admin user: admin@admin.com
    password: admin1234
    The PostgreSQL username: galaxy, password: galaxy, database name: galaxy
For more details,please visit: https://docs.galaxyproject.org/en/latest/admin/config.html
#### Browser access to the server:
    http://YOUR_IP_ADDRESS:8080

