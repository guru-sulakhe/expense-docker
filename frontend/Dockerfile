FROM nginx
# Removing default index.html from nginx
RUN rm -rf /usr/share/nginx/html/index.html
# Removing default images configuration from nginx
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -rf /etc/nginx/conf.d/default.conf
# Copying expnse.conf to /etc/nginx/nginx.conf
COPY expense.conf /etc/nginx/nginx.conf
# Copying code/* to /usr/share/nginx/html/
COPY code/* /usr/share/nginx/html/