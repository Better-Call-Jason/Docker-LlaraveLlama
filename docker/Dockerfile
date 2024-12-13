FROM ubuntu:22.04

# Prevent interactive prompts
ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=UTC

# Install system dependencies
RUN apt-get update && apt-get install -y \
    software-properties-common \
    curl \
    git \
    nano \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Install Node.js 20.x
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g npm@latest

# Add PHP repository and install PHP
RUN add-apt-repository -y ppa:ondrej/php \
    && apt-get update \
    && apt-get install -y \
    php8.1 \
    php8.1-curl \
    php8.1-xml \
    php8.1-mbstring \
    php8.1-zip \
    php8.1-common \
    && rm -rf /var/lib/apt/lists/*

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set working directory
WORKDIR /var/www/html

# Clone the repository (docker_build branch)
RUN rm -rf * && git clone https://github.com/Better-Call-Jason/LlaraveLlama.git . && rm -rf .git

# Set permissions
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html/storage

# Install PHP dependencies
RUN composer install --no-interaction --no-dev --optimize-autoloader

# Install Node.js dependencies and build assets
RUN npm install && npm run prod

# Copy environment file
RUN cp .env.example .env

# Generate application key
RUN php artisan key:generate

# Create entrypoint script
RUN echo '#!/bin/bash\n\
set -e\n\
\n\
# Colors for output\n\
RED="\033[0;31m"\n\
GREEN="\033[0;32m"\n\
YELLOW="\033[1;33m"\n\
NC="\033[0m"\n\
\n\
echo -e "${YELLOW}Starting LlaraveLlama initialization...${NC}"\n\
\n\
# Start Laravel\n\
echo -e "${GREEN}Starting Laravel server...${NC}"\n\
php artisan serve --host=0.0.0.0 --port=8000' > /usr/local/bin/docker-entrypoint.sh \
    && chmod +x /usr/local/bin/docker-entrypoint.sh

EXPOSE 8000

ENTRYPOINT ["/usr/local/bin/docker-entrypoint.sh"]