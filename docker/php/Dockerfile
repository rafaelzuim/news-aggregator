FROM php:fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

    # Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
  && export PATH=$PATH:/usr/local/bin

# Set the working directory
WORKDIR /var/www/html

# Copy the application code
COPY . /var/www/html

# Set proper permissions
RUN chown -R www-data:www-data /var/www/html