FROM nginx
# Removing default index.html from nginx
RUN rm -rf /usr/share/nginx/html/index.html
# Removing default images configuration from nginx
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -rf /etc/nginx/conf.d/default.conf
# allowing non-root access for nginx container
RUN mkdir -p /var/cache/nginx/client_temp && \
        mkdir -p /var/cache/nginx/proxy_temp && \
        mkdir -p /var/cache/nginx/fastcgi_temp && \
        mkdir -p /var/cache/nginx/uwsgi_temp && \
        mkdir -p /var/cache/nginx/scgi_temp && \
        chown -R nginx:nginx /var/cache/nginx && \
        chown -R nginx:nginx /etc/nginx/ && \
        chmod -R 755 /etc/nginx/ && \
        chown -R nginx:nginx /var/log/nginx
RUN touch /var/run/nginx.pid && \
chown -R nginx:nginx /var/run/nginx.pid /run/nginx.pid
COPY expense.conf /etc/nginx/nginx.conf
# Copying code/* to /usr/share/nginx/html/
COPY code /usr/share/nginx/html/
USER nginx
