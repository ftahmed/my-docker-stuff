FROM golang:latest

RUN go get -v -x github.com/nsec/the-internet
#RUN find / -name lxd -exec ls -lh {} \;
RUN find /go/pkg/linux_amd64/github.com/lxc/lxd -ls
RUN echo "root:1000000:65536" | tee -a /etc/subuid /etc/subgid && /go/pkg/linux_amd64/github.com/lxc/lxd
RUN mkdir -p /data/the-internet && the-internet create /data/the-internet

CMD the-internet start

# the-internet generate-map /data/map-of-the-internet
# the-internet stop
# the-internet destroy
