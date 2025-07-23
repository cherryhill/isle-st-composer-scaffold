# 🍒 Cherry Hill ISLE Site Template Scripts

Use these scripts to manage the ISLE Site Template project.

## Sync the production database to the local drupal-dev container

Run the `./scripts/ssh-sync` with an argument for the SSH host. For example:

```sh
./scripts/ssh-sync username@project-isle-st.example.net
```

The script will create a `backups` directory in the project root, which should be excluded in the `.gitignore` file. For each run of the `ssh-sync` script, a datestamp-named directory will be downloaded into the `backups` directory that contains exported configuration files and a database dump from the production site.

The databaase dump will be imported into the local development site.

If `config_split` is set up on the site, any split configs for the environment will be imported.

The site config will be immediately exported from the newly imported database, giving you an opportunity to capture configuration changes from production in version control.
