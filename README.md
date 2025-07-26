# 🍒 Cherry Hill ISLE Site Template Composer Scaffold

Use this project to keep Cherry Hill scaffolding up to date in ISLE Site Template projects.

## Setup

**Requirements:**
- [`jq`](https://jqlang.org/download/) must be installed.

### Add the repository

```sh
curl -fsSL https://raw.githubusercontent.com/cherryhill/edit-composer-json/3.x/repositories | bash -s -- -f drupal/rootfs/var/www/drupal/composer.json cherryhill/isle-st-composer-scaffold
```

Result:

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

---

### Add the script

```sh
curl -fsSL https://raw.githubusercontent.com/cherryhill/edit-composer-json/3.x/scripts | bash -s -- -f drupal/rootfs/var/www/drupal/composer.json -s post-update-cmd:./vendor/cherryhill/isle-st-composer-scaffold/spackle
```

Result:

```json
{
    "scripts": {
        "post-update-cmd": "./vendor/cherryhill/isle-st-composer-scaffold/spackle"
    }
}
```

### Require the 3.x branch of the project:

```bash
docker compose exec drupal-dev composer require cherryhill/isle-st-composer-scaffold:3.x-dev
```

### Run the spackle script:

```bash
docker compose exec drupal-dev composer run-script post-update-cmd
```

This will create an `assets/scripts` directory inside the Drupal root and a symlink to it in the project root.

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

## Usage

When `composer update` is run any updated scaffold files will be moved into place.

```bash
docker compose exec drupal-dev composer update cherryhill/isle-st-composer-scaffold
```
