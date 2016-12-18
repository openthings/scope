#FROM alpine:3.3
#FROM aarch64/alpine:edge
FROM openthing/ubuntu-rock:ARM64

MAINTAINER Weaveworks Inc <help@weave.works>
LABEL works.weave.role=system

WORKDIR /home/weave
#RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >>/etc/apk/repositories && \
#	apk add --update bash runit conntrack-tools iproute2 util-linux curl && \
#	rm -rf /var/cache/apk/*

RUN  echo "==========Building Docker for Scope Runtime.======"	
	apt-get install -y --update bash runit \
	iproute2 util-linux curl && \
	bison libc6 libltdl7 libnetfilter-conntrack3
#	conntrack-tools
#	apt-get autoremove 

#ADD ./docker.tgz /
ADD ./docker /usr/local/bin

ADD ./demo.json /
ADD ./weave /usr/bin/
COPY ./scope ./runsvinit ./entrypoint.sh /home/weave/
COPY ./run-app /etc/service/app/run
COPY ./run-probe /etc/service/probe/run
EXPOSE 4040
ENTRYPOINT ["/home/weave/entrypoint.sh"]
