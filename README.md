# drupal-compose

A minimal `compose.yaml` for deploying Drupal through [Soveryx](https://soveryx.com)'s
git-sync - paste this repo's URL into "Deploy from Git" and it boots a real,
working Drupal site: the official `drupal:10-apache` image plus a MariaDB
database, nothing else. Visit the deployed URL to walk through Drupal's own
installer.

Why this instead of markshust/docker-drupal's own compose file: that one
splits nginx/phpfpm/mysql/setup across four containers sharing one bind
mount, plus a one-shot `composer create-project` setup step - both real,
valid Compose patterns that need platform capabilities Soveryx doesn't have
yet (a volume shared across services in one group, and a run-once job-style
service). This repo's shape - one web container, one database, each with
its own disk - needs neither.
