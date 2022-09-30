FROM lcmchris1/thesillyhome-container:dev
#Add nginx and create the run folder for nginx.
RUN \
    apt-get install -y \
    nginx \
    && mkdir -p /run/nginx

#Copy our conf into the nginx http.d folder.
COPY ingress.conf /etc/nginx/http.d/

#Launch nginx with debug options.
CMD [ "nginx","-g","daemon off;error_log /dev/stdout debug;" ]