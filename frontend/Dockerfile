FROM nginx:1.24.0-alpine3.17-slim

RUN rm -rf /usr/share/nginx/html/ && \
    rm -rf /etc/nginx/conf.d/default.conf && \
    rm -rf /etc/nginx/nginx.conf

#Now creating the direcotry for nginx configuration and static content
RUN mkdir -p /var/cache/nginx/client_temp && \
    mkdir -p /var/cache/nginx/proxy_temp && \
    mkdir -p /var/cache/nginx/fastcgi_temp && \
    mkdir -p /var/cache/nginx/uwsgi_temp && \
    mkdir -p /var/cache/nginx/scgi_temp && \
    mkdir -p /etc/nginx/ssl/

#Now provide the ownership rights to nginx user account to write in the above created directories
RUN chown -R nginx:nginx /var/cache/nginx/ && \
    chown -R nginx:nginx /etc/nginx/ssl/ && \
    chown -R nginx:nginx /etc/nginx/ && \
    chown -R nginx:nginx /var/log/nginx

#Now provide the access permissions to nginx user account to write in the above created directories
RUN chmod -R 755 /var/cache/nginx/ && \
    chmod -R 755 /etc/nginx/ && \
    chmod -R 755 /var/log/nginx


COPY nginx.conf /etc/nginx/nginx.conf
RUN  chmod -R 755 /etc/nginx/nginx.conf
COPY static /usr/share/nginx/html/

RUN touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid

USER nginx
EXPOSE 80
ENTRYPOINT ["nginx"]
CMD [ "-g", "daemon off;" ]








# This script will be running on sudo (root user) priveligies
# FROM nginx:1.24
# RUN rm -rf /usr/share/nginx/html/ && \
#     rm -rf /etc/nginx/conf.d/default.conf && \
#     rm -rf /etc/nginx/nginx.conf
# COPY nginx.conf /etc/nginx/nginx.conf
# COPY static /usr/share/nginx/html/
# EXPOSE 80
# ENTRYPOINT ["nginx"]
# CMD ["-g", "daemon off;"]