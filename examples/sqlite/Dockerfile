ARG IMAGE_VERSION=beta-1.0.0

FROM osbre/frankenwp-php:$IMAGE_VERSION

# Install SQLite
RUN apt-get update && apt-get install -y --no-install-recommends sqlite3 libsqlite3-dev wget

# Install the SQLite plugin
RUN wget https://downloads.wordpress.org/plugin/sqlite-database-integration.zip -O /usr/src/wordpress/sqlite-database-integration.zip && \
    unzip /usr/src/wordpress/sqlite-database-integration.zip -d /var/www/html/wp-content/mu-plugins/ && \
    rm /usr/src/wordpress/sqlite-database-integration.zip

RUN  cp /var/www/html/wp-content/mu-plugins/sqlite-database-integration/db.copy /var/www/html/wp-content/db.php && \
    sed -i 's/{SQLITE_IMPLEMENTATION_FOLDER_PATH}/\/var\/www\/html\/wp-content\/mu-plugins\/sqlite-database-integration/g' /var/www/html/wp-content/db.php && \
    sed -i 's/{SQLITE_PLUGIN}/WP_PLUGIN_DIR\/SQLITE_MAIN_FILE/g' /var/www/html/wp-content/db.php
