FROM nginx:alpine

# Copy custom NGINX configuration file to the container
# This file replaces the default NGINX configuration with your custom settings in default.conf
COPY default.conf /etc/nginx/conf.d/default.conf

# Create a directory for storing SSL certificates
# The -p flag ensures the command succeeds even if the directory already exists
RUN mkdir -p /etc/nginx/ssl

# Copy the SSL certificate and key into the container for HTTPS support
# These files are used by NGINX to enable secure communication over HTTPS
COPY /ssl/nginx.crt /etc/nginx/ssl
COPY /ssl/nginx.key /etc/nginx/ssl
