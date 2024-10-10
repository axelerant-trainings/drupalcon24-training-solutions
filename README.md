#Drupal Headless Ecommerce

## Project Basic details

| Placeholder | Example |
| --- | --- |
| `#GIT_PRIMARY_DEV_BRANCH` | `develop` |
| `#GITHUB_PROJECT` | The "project" in https://github.com/axelerant-trainings/drupalcon24-training-solutions |
| `#JIRA_URL` | https://axelerant.atlassian.net/browse/LDT-962 |
| `#LOCAL_DEV_SITE_ALIAS` | `@drupalcon24` |
| `#LOCAL_DEV_URL` | https://drupalcon24.ddev.site/ |

## Tools & Prerequisites

The following tools are required for setting up the site. Ensure you are using
the latest version or at least the minimum version mentioned below.
* [Composer](https://getcomposer.org/download/) - v2.6.2
* [Docker](https://docs.docker.com/install/) - V4.7.0
* [DDEV-Local](https://ddev.readthedocs.io/en/stable/#installation) - v1.23.1
* [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) - v2.40.0


### Steps to setup project:

```bash
git clone git@github.com:axelerant-trainings/drupalcon24-training-solutions.git
```
Change to the directory of repository.

```bash
cd drupalcon24-training-solutions
```
Checkout to `develop` branch.

```bash
git checkout -b develop origin/develop
```
Once authenticated, run the following command to start the application.

```bash
ddev start
```
Once DDEV has been setup successfully, it will display the links in the
terminal. Next, run the following to fetch all dependencies.

```bash
ddev composer install
```

Import base DB, make sure yo have your DB in current folder drupalcon24-training-solutions.
```bash
ddev import-db --file=drupalcon24.sql.gz
```

Clear cache.

```bash
ddev drush cr
```

Import configuration
```bash
ddev drush cim
```

Clear cache again.
```bash
ddev drush cr
```

Generate a one time login link and reset the password through it.

```bash
ddev drush uli
```
Or directly launch the site 
```bash
ddev launch $(ddev drush uli)
```

Congratulations! You can now access the site at: [https://drupalcon24.ddev.site/](https://drupalcon24.ddev.site/).
