#  Unofficial Oracle Linux systemd docker container

The container was created based on (https://github.com/CentOS/CentOS-Dockerfiles/tree/master/systemd/centos7).

## Sample httpd container

Here we show you how we can create a sample httpd container.

Frist create a Dockerfile and setup the required service or services. Systemd can launch multiple services.

```
FROM sirkkalap/oraclelinux-systemd

MAINTAINER "Your Name" <you@example.com>

RUN yum -y install httpd; yum clean all; systemctl enable httpd.service

EXPOSE 80

CMD ["/usr/sbin/init"]
```

Then build it.

```
docker build --rm --no-cache -t httpd .
```

Launch it.

```
docker run --privileged --name httpd -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 80:80 -d  httpd
```

Finally use it.
