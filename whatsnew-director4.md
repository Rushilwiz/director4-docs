---
Title: What's new in Director 4.0
...

# What's new in Director 4.0

If you were used to Director 3, Director 4.0 attempts to remain relatively compatible and preserve certain workflows. However, it is important to note that Director 4.0 is a rewrite, aiming to take advantage of new technologies and fixing fundamental design flaws from Director 3. Director 4.0 functions quite differently, and users should be aware of this.

This page only summarizes the most important user-visible changes in Director 4.0. If you have any questions or concerns, please feel free to contact us at [director@tjhsst.edu](mailto:director@tjhsst.edu).

## New features

- Your site now runs inside a Docker container. From the Image Selection page (see [Site Configuration](/quick-start/site-configuration.md) for details), you can select a Docker image, as well as choosing any extra packages you want to install.

## Changes that may require intervention

- You will need to select a Docker image for your site to work properly. See [Site Configuration](/quick-start/site-configuration.md) for details.
- If you had a Python virtual environment, you'll need to destroy and recreate it -- the Python Docker images have newer versions of Python, and that breaks virtualenvs.
- If you were relying on packages that were installed system-wide on Director 3.0 (like Django), you'll need to start using a virtual environment (and/or install some of them on the Image selection page).
- You cannot hardcode your site's database URL ([here's why](/databases/no-hardcode-url.md)).
- It is no longer possible to select a custom run script. Your run script must be named `run.sh` and located in either 1) the main site directory, 2) your site's `private` directory, or 3) your site's `public` directory. (If more than one of these is present, the first one found takes precendence.)

## Features that are no longer supported

- Git integration has been removed because the new Director 4.0 architecture makes it more difficult to implement and we saw limited usage. Currently, there are no plans to add Git integration.
  If you require Git, install it from the "Configure Docker Image" page by adding `git` to the list of packages at the bottom of the page. See [this page](../best-practices/version-control) for more information.
- The buttons for exporting/importing databases have been removed. You can still export/import databases, but you'll need to use `mysqldump`/`pg_dump` (exporting) and `mysql`/`psql` (importing) manually from the command line.
