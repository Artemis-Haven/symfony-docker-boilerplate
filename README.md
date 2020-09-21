# Symfony 5 Boilerplate

```bash
git clone https://github.com/Artemis-Haven/symfony-docker-boilerplate.git YOURPROJECTNAME
cd YOURPROJECTNAME
rm code/.gitkeep
git clone https://github.com/Artemis-Haven/symfony-boilerplate.git code
docker-compose run php composer install
docker-compose run node yarn install
docker-compose up -d
docker-compose run php php bin/console doctrine:schema:create
```