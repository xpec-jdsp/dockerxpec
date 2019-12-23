FROM ubuntu:16.04

RUN apt-get update \
&& apt-get install -y supervisor \
&& mkdir -p /var/log/supervisor \
&& apt-get -y install varnish \
&& rm /etc/varnish/default.vcl \
&& rm /etc/default/varnish 
EXPOSE 443 80
CMD ["/usr/bin/supervisord"]
