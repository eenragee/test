FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p egorbatasov.com/img && \
    chmod -R 754 /var/www/egorbatasov.com/ && \
    useradd Egor && groupadd Batasov && usermod -aG Batasov Egor && \
    chown -R Egor:Batasov /var/www/egorbatasov.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/egorbatasov.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Egor/g' /etc/nginx/nginx.conf
ADD index.html /var/www/egorbatasov.com/
ADD img.jpg /var/www/egorbatasov.com/img/
CMD ["nginx", "-g", "daemon off;"]
