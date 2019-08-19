# os-installation-documents
    Suppose want to install Ubutun Linux
    
    1-download unetbootin
    https://unetbootin.github.io/

    2-download OS image (iso) file.
    https://ubuntu.com/download/desktop

    3-open unetbootin and make bootable pendrive for other machine/ make bootable folder for self machine.

    4- restart system and follow screen steps.



# os-VitualBoxLinux-connection via putty.

       1) Make sure ssh client is installed on your Linux. If not,install ssh client.

       amir@amir-VirtualBox:~$ ssh -V
       OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017

       if not exist please install using below command.
       sudo apt update
       sudo apt install openssh-server

       2) Power off the OS.

       3) Now on your VirtualBox(used- Version 6.0.6 r130049 (Qt5.6.2)) 
       go to Settings -> Network -> Adapter1 
       a) checked enable network adapter
       b) Attached to : Bridge Adapter
       c) Name: Intel(R) Ethernet connection.

       4) Now start your OS. Run ifconfig /ip a , now the inet address is your IP from enp0s3 section.
       Use this and run it on your putty. Login with your credentials.




---------------------------------------------------------------------
core level package manager
-----------------------------
There are two type of distrubution based on core package manager in linux
1) dpkg  OS like (Debian,ubuntu)
2) rpm   OS like (Centos,Fedora)

top level packager manager os wise
----------------------------------
for debian and ubuntu
---------------------
    apt-get(all except searching) ,apt-cache ( for searching and showing details)

    0) update the package index file
        sudo apt-get update

            When this command is run, all available packages are fetched and re-indexed from the locations specified in /etc/apt/sources.list and /etc/apt/sources.list.d/.


    0) how to checked installed package in system
        dpkg -l 'pattern'
        example :
        dpkg -l '*mysql*'
    
    1) for seraching all available package for your system
        apt-cache pkgnames

    2) for seraching perticular package

        apt-cache search [pkg-name-pattern]  

    3) for perticular package information (like size & all)
        apt-cache show [package-name]

    4) for Installing package
        sudo apt-get install [package-name]

    5) remove package without configuration.
        sudo apt-get remove [package-name]

    6) remove package with all configuration.
        sudo apt-get --purge remove [package-name]   
        

how to install downloaded package
-----------------------------------
    if you have file called .tar.gz file  or .tar file

    1) tar xvfz filename.tar.gz   or tar xvf filename.tar
    2) goto extract file and run ./configure (if configure file is not there check readme file)
    3) make
    4) make install
    


ENVIRONEMENT VARIABLE IN LINUX
----------------------------------
    It is case sensitive ..means PATH and path both are different

        1) how to see/check all
        printenv   
        2) how to see perticular
        printenv name or echo $name
        example :
        a) printenv PATH
        b) echo $PATH
        
        
        
        




for more details visit to given url 
---------------------------------------
    https://blog.packagecloud.io/eng/2015/03/30/apt-cheat-sheet/
    
    
    
    

DOCKER 
---------------
       Docker is a set of platform-as-a-service products that use operating-system-level virtualization to deliver software in packages        called containers

DOCKER HUB
-----------
it is place where we store docker image and used to setup application anywhere without worrying the app dependency.

How Docker Works
----------------
1) setup docker clinet into machine
2) create image application along with required dependency 
3) copy this image to target machine
4) make setup of application quickly with the help of image .

    
 DOCKER SETUP on UBUNTU
 ---------------------------

    1) to get update the repository of packages
    sudo apt-get update

    2) uninstall exiting old one
    sudo apt-get remove docker docker-engine docker.io

    3) install new one
    sudo apt install docker.io

    4) check install version
    docker --version

    5)start stop status of docker
    sudo systemctl status docker
    sudo systemctl stop docker
    sudo systemctl start docker
    
    
    
 some operation with existing docker images
 ------------------------------------------ 
 
how to download docker image from docker hub
-----------------------------------------------
    docker pull image-name
    example: sudo docker pull busybox

how to remove docker image from docker
-----------------------------------------------
    docker rmi image-name
    example: sudo docker rmi busybox


how to check existing images in system
---------------------------------------------
    sudo docker images


how to run images as a container
-------------------------------
    sudo docker run image-name

    example :
    sudo docker run busybox

    run wtih --rm so we can remove container when it stopped

    example:
    sudo docker run --rm busybox

how to see running container id
-------------------------------
    docker ps -a


how to stop all running docker container
-------------------------------------
    docker system prune


how to remove perticualr container
----------------------------------------
    docker container rm cc3f2ff51cab cd20b396a061
    or 
    docker rm cc3f2ff51cab cd20b396a061

    
    


How to create custom image
--------------------------------
    1) create Dockerfile 
    this file will have set of instruction to build a image file 

    for sample  i used 2 commands

    a) FROM this will use to take base image from dockerhub
    b) RUN this will execute while running docker containers

    I created Dockerfile and put below command inside file.

    FROM ubuntu
    RUN apt-get update && apt-get install tree



    after that i hit docker build command

    2) sudo docker build -t mytree .
    Note:
    -t use to give tagname of image . is directory location where Dockerfile will be present.


    3) To See build images
    amir@amir-VirtualBox:~/docker-rnd$ sudo docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
    mytree              latest              8c240bfdd1ca        About a minute ago   92.1MB
    ubuntu              latest              a2a15febcdf3        4 days ago           64.2MB



    4) How to run Images
    sudo docker run -it imageid/name

    example:

    sudo docker run -it 8c240bfdd1ca





