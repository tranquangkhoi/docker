FROM httpd:2.4

# Cập nhật và cài đặt vim, htop

RUN apt-get update -y \
    && apt-get install vim -y \
    && apt-get install htop \
    && rm -rf /var/lib/apt/lists/*

# Copy các file dữ liệu, cấu hình vào image
ADD ./httpd.conf /usr/local/apache2/conf/httpd.conf
ADD ./httpd-vhosts.conf /usr/local/apache2/conf/extra/httpd-vhosts.conf

# Mở cổng 80, 443 trên network container nối vào

EXPOSE 80 443

CMD [ "httpd-foreground"]