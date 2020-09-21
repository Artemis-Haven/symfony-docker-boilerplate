# Symfony 5 Docker Boilerplate

This is a Docker boilerplate to quickly run a Symfony app. It includes:
- PHP-FPM
- Nginx
- MySQL
- Adminer
- Node & Yarn to use with Webpack Encore

**It is intended to be used in association with this other repository :** https://github.com/Artemis-Haven/symfony-boilerplate but it can also be used independently.

With these two repos, **in less than one minute, you can deploy a fully working, ready-to-use, dev environment for a new Symfony project.**

The other repository contains:
- A Symfony 5.1 skeleton with a clean templates structure
- A custom AdminAuthenticator
- EasyAdminBundle, with CkEditor and ElFinder to get WYSIWYG text fields
- Custom Twig functions to quickly fill the website content from the admin page
- Webpack Encore configured to compile JS and SASS (with hot reloading)

---

## Prerequisites

You need Docker & Docker-Compose.

Make sure that the ports 8010 to 8015 are not used on your computer.

## Installation

Clone the repository of the Docker boilerplate.
Replace YOURPROJECTNAME with the name of the root folder of your new project.

```bash
git clone https://github.com/Artemis-Haven/symfony-docker-boilerplate.git YOURPROJECTNAME
cd YOURPROJECTNAME
```

Then clone the repository of the source code Symfony webapp. 

```bash
rm code/.gitkeep
git clone https://github.com/Artemis-Haven/symfony-boilerplate.git code
```

Install the PHP & Javascript dependencies.

```bash
docker-compose run php composer install
docker-compose run node yarn install
```

Start the containers.

```bash
docker-compose up -d
```

Wait a few seconds and create the database tables.

```bash
docker-compose run php php bin/console doctrine:schema:create
```

It's done! Your website is now available at http://localhost:8010

You can also manage your database with Adminer at http://localhost:8012

Your JS and SASS files will be automatically compiled because the hot reloading is already started!
