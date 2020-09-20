FROM node:latest

WORKDIR /var/www/symfony

RUN curl -o- -L https://yarnpkg.com/install.sh | bash

RUN yarn install

CMD ["yarn", "encore", "dev", "--watch"]
