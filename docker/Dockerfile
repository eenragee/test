FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p daniilsemin.com/img && \
    chmod -R 754 /var/www/daniilsemin.com/ && \
    useradd Daniil && groupadd Semin && usermod -aG Semin Daniil && \
    chown -R Egor:Batasov /var/www/daniilsemin.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/daniilsemin.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Daniil/g' /etc/nginx/nginx.conf
ADD index.html /var/www/daniilsemin.com/
ADD img.jpg /var/www/daniilsemin.com/img/
CMD ["nginx", "-g", "daemon off;"]