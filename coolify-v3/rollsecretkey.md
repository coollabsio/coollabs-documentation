---
head:
  - - meta
    - name: description
      content: Coolify - Destinations
  - - meta
    - name: keywords
      content: destinations coollabs coolify
  - - meta
    - name: twitter:card
      content: summary_large_image
  - - meta
    - name: twitter:site
      content: "@heyandras"
  - - meta
    - name: twitter:title
      content: Coolify
  - - meta
    - name: twitter:description
      content: An open-source & self-hostable Heroku / Netlify alternative.
  - - meta
    - name: twitter:image
      content: https://cdn.coollabs.io/assets/coollabs/og-image-documentation.png
  - - meta
    - property: og:type
      content: website
  - - meta
    - property: og:url
      content: https://coolify.io
  - - meta
    - property: og:title
      content: Coolify
  - - meta
    - property: og:description
      content: An open-source & self-hostable Heroku / Netlify alternative.
  - - meta
    - property: og:site_name
      content: Coolify
  - - meta
    - property: og:image
      content: https://cdn.coollabs.io/assets/coollabs/og-image-documentation.png
---

# Roll Secret Key

In `v3.12.33` a new feature has been added. You can now roll your secret key.

This is useful if you think your secret key has been compromised.

::: warning
It is introduced because there was a security issue with the secret key. If you are using a version below v3.12.33, please update your Coolify instance.

Technical details: The secret key was generated with the installation date used as a random seed. This means that if someone knows the installation date, they can generate the secret key. This is not a problem if you are using a recent version of Coolify, because the installation date is not used anymore since 2023.07.14.

:::

## How to roll the secret key

If you are upgrading form a version below `v3.12.33`, you will be automatically rolled to a new secret key.

If you are just installing Coolify, you do not need to do anything.

## Rollback to old secret key

(It also solve this [issue](https://github.com/coollabsio/coolify/issues/1148) related to **secretOrPrivateKey must be an asymmetric key when using RS256** or **Getting 500 error when accessing running services**).

If you want to rollback to the old secret key, you need to do the following:

1. Login to your Coolify instance via SSH.
2. Switch to root user (`sudo su -`) and locate your `~/coolify/.env` file. 
3. In `~/coolify/.env` file there should be a `COOLIFY_SECRET_KEY` environment variable.
4. Create a `COOLIFY_SECRET_KEY_BETTER` with the same value as `COOLIFY_SECRET_KEY`.
5. Check your database files with `docker exec coolify ls -l /app/db` command.
6. There should be at least on with the name of `prod.db` and a few with `prod.db_<date>`.
7. Locate the oldest one. For example:
```
-rw-r--r-- 1 root root 7901184 Aug 23 09:30 prod.db
-rw-r--r-- 1 root root 7901184 Jul 18 10:09 prod.db_1689674942980 <- THIS (date could be different)
```
8. Make a copy of your `prod.db` file: `docker exec coolify cp /app/db/prod.db /app/db/prod.db_$(date +"%Y%m%d%H%M%S")`
9. Overwrite `prod.db` with the old database file: `docker exec coolify cp /app/db/prod.db_1689674942980 /app/db/prod.db`

::: warning
`app/db/prod.db_1689674942980` will be different in your case
:::

10. Reinstall Coolify with: `cd ~ && wget -q https://get.coollabs.io/coolify/install.sh -O install.sh; sudo bash ./install.sh -f`

If you have any questions, please [contact us](../contact.md).

## Force roll secret key

1. Login to your Coolify instance via SSH.
2. Run the following command: `docker exec -ti coolify bash`. Now you are in the Coolify container.
3. You will work in the `/app/.env` file. You can edit it with `vi .env`.
4. Delete `COOLIFY_SECRET_KEY_BETTER`.
5. Login to your Coolify instance on the web interface.
6. Go to `Settings` and fill the `Rollback` input field with `3.12.33` (or the latest version - you can check it [here](https://get.coollabs.io/versions.json)) and click on `Rollback`.

If you have any questions, please [contact us](../contact.md).

