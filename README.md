# Install magento
php bin/magento setup:install \
--base-url=http://localhost:8080 \
--db-host=mysql \
--db-name=magento \
--db-user=root \
--db-password=abc123 \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=tranquangkhoi@luvina.net \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=elasticsearch7  \
--elasticsearch-host=elasticsearch7  \
--elasticsearch-port=9200


php bin/magento module:disable {Magento_Elasticsearch,Magento_InventoryElasticsearch,Magento_Elasticsearch6,Magento_Elasticsearch7}

chmod -R 777 var

php bin/magento setup:di:compile

php bin/magento cache:clean