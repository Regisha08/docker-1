FROM debian

WORKDIR /home/teamspeak

EXPOSE 9987/udp 30033 10011

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y wget bzip2 && \
    wget https://files.teamspeak-services.com/releases/server/3.10.2/teamspeak3-server_linux_amd64-3.10.2.tar.bz2 && \
    tar xfv teamspeak3-server_linux_amd64-3.10.2.tar.bz2 && \
    mv ./teamspeak3-server_linux_amd64/* . && \
    rm -rf teamspeak3-server_linux_amd64-3.10.2.tar.bz2 && \
    touch .ts3server_license_accepted

ENTRYPOINT sh ts3server_minimal_runscript.sh

#~/01_dockerfiles/ex01	docker build -t ex01 .

# docker run --rm -ti -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ex01