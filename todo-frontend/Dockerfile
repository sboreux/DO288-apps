FROM registry.access.redhat.com/ubi8:8.0

LABEL version="1.0" \
      description="To Do List application front-end" \
      creationDate="2017-12-25" \
      updatedDate="2019-08-01" \
      io.openshift.tags="frontend nginx" \
      io.k8s.description="frontend image for todo app" \
      io.openshift.exposeservices="8080:todo-frontend"

ENV BACKEND_HOST=localhost:8081

RUN yum install -y --disableplugin=subscription-manager --nodocs \
        nginx nginx-mod-http-perl && \
    yum clean all && \
    touch /run/nginx.pid && \
    chgrp -R 0 /var/log/nginx /run/nginx.pid && \
    chmod -R g=u /var/log/nginx /run/nginx.pid
  
COPY nginx.conf /etc/nginx/
COPY src/ /usr/share/nginx/html

EXPOSE 8080

CMD nginx -g "daemon off;"

