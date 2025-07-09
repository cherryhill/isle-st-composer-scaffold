# 🍒 Cherry Hill ISLE Site Template Composer Scaffold

Use this project to keep Cherry Hill scaffolding up to date in ISLE Site Template projects.

## Setup

From the project root run the setup script:

```bash
curl -fsSL https://raw.githubusercontent.com/cherryhill/isle-st-composer-scaffold/2.x/setup | bash
```

This will automatically:

- Add this custom repository to your `composer.json`
- Add the `post-update-cmd` script to your `composer.json`
- Create an `assets/scripts` directory inside the Drupal root and a symlink to it in the project root

```json
{
    "repositories": [
        {
            "type": "github",
            "url": "https://github.com/cherryhill/isle-st-composer-scaffold"
        }
    ]
}
```

```json
{
    "scripts": {
        "post-update-cmd": "./vendor/cherryhill/isle-st-composer-scaffold/spackle"
    }
}
```

```tree
<project>
├── certs/
├── drupal/
│   └── rootfs/
│       └── var/
│           └── www/
│               └── drupal/
│                   ├── assets/
│                   │   └── scripts/
│                   ├── config/
│                   └── web/
├── scripts -> drupal/rootfs/var/www/drupal/assets/scripts/
└── secrets/
```

Then, require the 2.x branch of the project:

```bash
docker compose exec -T drupal-dev with-contenv bash -lc 'composer require cherryhill/isle-st-composer-scaffold:2.x-dev'
```

## Usage

Now, when `composer update` is run updated scaffold files will be moved into place:

```bash
docker compose exec -T drupal-dev with-contenv bash -lc 'composer update cherryhill/isle-st-composer-scaffold'
```
