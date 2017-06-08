FROM php:5.6.30-fpm
LABEL Kyben C. de Guia <kc.deguia@gmail.com>

ENV PHALCON_VERSION=3.1.2

# Compile Phalcon
RUN set -xe && \
        curl -LO https://github.com/phalcon/cphalcon/archive/v${PHALCON_VERSION}.tar.gz && \
        tar xzf v${PHALCON_VERSION}.tar.gz && cd cphalcon-${PHALCON_VERSION}/build && ./install && \
        echo "extension=phalcon.so" > /usr/local/etc/php/conf.d/phalcon.ini && \
        cd ../.. && rm -rf v${PHALCON_VERSION}.tar.gz cphalcon-${PHALCON_VERSION} && \
        # Insall Phalcon Devtools, see https://github.com/phalcon/phalcon-devtools/
        curl -LO https://github.com/phalcon/phalcon-devtools/archive/v${PHALCON_VERSION}.tar.gz && \
        tar xzf v${PHALCON_VERSION}.tar.gz && \
        mv phalcon-devtools-${PHALCON_VERSION} /usr/local/phalcon-devtools && \
		ln -s /usr/local/phalcon-devtools/phalcon.php /usr/local/bin/phalcon


# Compile Composer
Run php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
	php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && \
	php composer-setup.php && \
	php -r "unlink('composer-setup.php');" && \
	mv composer.phar /usr/local/bin/composer


# Install Git, Node, Npm, Bower, wget, build-essential, tcl8.5
RUN apt-get update && \
	  apt-get install -y git nodejs-legacy npm wget build-essential tcl8.5 && \
	  npm install -g bower && \
    rm -rf /var/lib/apt/lists/*

# Install Robo PHP Task Runner && Redis
Run wget http://robo.li/robo.phar && chmod +x robo.phar && mv robo.phar /usr/bin/robo && \
    wget http://download.redis.io/releases/redis-stable.tar.gz && tar xzf redis-stable.tar.gz && cd redis-stable && make && make test && make install && cd utils && ./install_server.sh && service redis_6379 start
