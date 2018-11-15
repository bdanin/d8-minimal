# Drupal 8 Minimal Starter
By Brian Danin

## Pre-requisites
- Git, and some basic command-line (CLI) *nix skills
- Lando installed for development, see [devwithlando.io](https://docs.devwithlando.io/installation/installing.html)
  - Docker is required for Lando development

## Getting Started
Clone this repo, and then run:

```bash
lando start
```

Navigate to the resulting URL, and install the Drupal database.

Enter the default Drupal 8 credentials:
- 'database' => 'drupal8'
- 'username' => 'drupal8'
- 'password' => 'drupal8'
- 'host' => 'database'

Install using the **minimal** profile.

### First Config:Import
First, config_suite needs to be turned on, please run:
```bash
lando drush en config_suite -n
```

Now, the configuration can be imported. This package has an update command that will install composer requirements and update config:
```bash
lando update
```

### Congratulations!
Hopefully everything is working as expected. You can use drush to login:
```bash
lando drush uli
```
after the word `default` in the above output, copy-paste the resulting path on your local URL to login to Drupal.

## Useful Commands
The below commands are often used to help work with Drupal 8.

### Local debugging
Turn on debugging and make local development easier:
```bash
lando drupal site:mode dev
```
Often a warning will popup that will say the services.yml cannot be re-written. This can be fixed on a local install with:
```bash
chmod -R 775 docroot/sites/default
```
and then re-run the `lando drupal site:mode dev` command.

### Add a Project
```bash
lando composer install drupal/PROJECT_NAME
```

Install with:
```bash
lando drush en PROJECT_NAME -n
```

Export this to code:
```bash
lando drush cex sync -n
```

### Export (or Import) a Database
```bash
lando db-export
```

If you already have a database file:
```bash
lando db-import name-of-file.ext
```
