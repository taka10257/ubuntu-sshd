FROM       ubuntu:16.04
MAINTAINER takamasa suzuki "https://github.com/taka10257"

RUN apt-get update

RUN apt-get install -y sudo

RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

# タイムゾーンの変更
RUN apt-get install -y tzdata

#ENV TZ America/New_York
ENV TZ Asia/Tokyo
#ENV TZ America/Chicago
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone


EXPOSE 22

# for nginx
EXPOSE 80

CMD    ["/usr/sbin/sshd", "-D"]
