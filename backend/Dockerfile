#FROM golang:1.7.1
FROM openthings/ubuntu-golang:ARM64

RUN apt-get update && \
	apt-get install -y libpcap-dev python-requests time file shellcheck && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN go clean -i net && \
	go install -tags netgo std 
	#go install -race -tags netgo std

ENV GIT_SSL_NO_VERIFY=true
ENV http_proxy 192.168.1.88:9999

#RUN go get -tags netgo \
#		github.com/fzipp/gocyclo \
#		github.com/golang/lint/golint \
#		github.com/kisielk/errcheck \
#		github.com/mjibson/esc \
#		github.com/client9/misspell/cmd/misspell && \
#	rm -rf /go/pkg/ /go/src/

RUN git clone --progress https://github.com/golang/lint \
	"$GOPATH/src/github.com/golang/lint" &&\
    git clone --progress https://github.com/fzipp/gocyclo \
	"$GOPATH/src/github.com/fzipp/gocyclo" &&\
    git clone --progress https://github.com/client9/misspell \
	"$GOPATH/src/github.com/client9/misspell" &&\
    git clone --progress https://github.com/kisielk/errcheck \
	"$GOPATH/src/github.com/kisielk/errcheck" &&\
    git clone --progress https://github.com/mjibson/esc \
	"$GOPATH/src/github.com/mjibson/esc"

COPY build.sh /
ENTRYPOINT ["/build.sh"]
