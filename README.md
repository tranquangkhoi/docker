# Install magento
php bin/magento setup:install \
--base-url=http://localhost \
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
--use-rewrites=1


php bin/magento module:disable {Magento_Elasticsearch,Magento_InventoryElasticsearch,Magento_Elasticsearch6,Magento_Elasticsearch7}