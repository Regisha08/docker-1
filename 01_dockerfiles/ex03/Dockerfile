#https://gitlab.com/gitlab-org/gitlab-ce
#https://about.gitlab.com/install/#debian

FROM debian

RUN apt-get update && \
		apt-get -y upgrade && \
		apt-get -y install wget openssh-server ca-certificates postfix

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && \
		chmod 777 script.deb.sh && ./script.deb.sh
#chmod 777 gives all the permitions to the script script.deb.sh
					#run the script
#RUN					apt-get install -y gitlab-ce
RUN apt-get install -y gitlab-ce tzdata

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && sleep 5 && gitlab-ctl reconfigure && tail -f /dev/null

# How to build it?
# docker build -t ex03 .

# How to run it?
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03