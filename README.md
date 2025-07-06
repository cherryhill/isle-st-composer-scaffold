# 🍒 Cherry Hill ISLE Site Template Composer Scaffold

Use this project to keep Cherry Hill scaffolding up to date in ISLE Site Template projects.

First, run the setup script:

```sh
curl -fsSL https://raw.githubusercontent.com/cherryhill/isle-st-composer-scaffold/main/setup | bash
```

This will create a `./drupal/rootfs/var/www/drupal/assets/scripts` directory and a symlink `./scripts` to it. It will also add the scaffold project to the repositories list and add a `post-update-cmd` to scripts list.

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
        "post-update-cmd": "./vendor/cherryhill/isle-st-composer-scaffold/assemble"
    }
}
```

Then, require the project:

```sh
docker compose exec -T drupal-dev with-contenv bash -lc 'composer require cherryhill/isle-st-composer-scaffold'
```

Now, when `composer update` is run our scaffold files will be moved into place:

```sh
docker compose exec -T drupal-dev with-contenv bash -lc 'composer update cherryhill/isle-st-composer-scaffold'
```
