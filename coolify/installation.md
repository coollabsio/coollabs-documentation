---
head:
  - - meta
    - name: description
      content: Coolify - Installation
  - - meta
    - name: keywords
      content: installation coollabs coolify
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

# Installation

This section provide details on how to install Coolify.

Before running the install script, please ensure your server is updated and has the following packages installed:

- `sudo`
- `wget`
- `curl`


```bash
sudo su
```

```bash
apt update && apt -y upgrade && apt -y install curl wget sudo
```

## Scripted

Prompts for answers:

```bash
wget -q https://get.coollabs.io/coolify/install.sh \
-O install.sh; sudo bash ./install.sh
```

No question asked (force):

```bash
wget -q https://get.coollabs.io/coolify/install.sh \
-O install.sh; sudo bash ./install.sh -f
```

Opt-out from telemetry (count installed instances on the [landing page](https://coolify.io))

```bash
wget -q https://get.coollabs.io/coolify/install.sh \
-O install.sh; sudo bash ./install.sh -n
```

You can review the script [here](https://github.com/coollabsio/get.coollabs.io/blob/main/static/coolify/install.sh).

## Manually

1. Need to set the required environment variables in a `.env` file (see
   [below](./installation.md#environment-variables))
2. Need to have [Docker Engine v20.10+](https://docs.docker.com/engine/install/)
   installed on your server.

### Environment Variables

Coolify needs to have the following environment variables to be set in advance.

> This is done automatically with the automated installation script.

```text
COOLIFY_APP_ID=
COOLIFY_SECRET_KEY=
COOLIFY_DATABASE_URL=file:../db/prod.db
COOLIFY_IS_ON=docker
COOLIFY_WHITE_LABELED=false
COOLIFY_WHITE_LABELED_ICON=
COOLIFY_AUTO_UPDATE=false
```

| Variable                   | Explanation                                                                                                                 |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| COOLIFY_APP_ID             | A random UUID. Used to differentiate between installed instances. Also used to enable/disable telemetry (empty = disabled). |
| COOLIFY_SECRET_KEY         | Used to encrypt all kinds of private data. **Must be `32` characters long**.                                                |
| COOLIFY_DATABASE_URL       | SQLite database URL. **Must be under `../db`** .                                                                            |
| COOLIFY_IS_ON              | Where Coolify is deployed to. Currently, only **`docker`** is supported.                                                    |
| COOLIFY_WHITE_LABELED      | It removes the "branding" of your Coolify instance. Please get in touch with me before using this.                          |
| COOLIFY_WHITE_LABELED_ICON | A remote icon to be replaced on the login/registration page.                                                                |
| COOLIFY_AUTO_UPDATE        | It updates your Coolify instance automatically behind the scenes.                                                           |

## Options

```sh
Usage: install.sh [options...]
    -h, --help                  Show this help menu.
    -v, --version               Show script version.

    -d, --debug                 Show debug logs during installation.
    -f, --force                 Force installation.

    -r, --restart               Only restarts Coolify.

    -n, --do-not-track          Opt-out of telemetry.
    # You can set export DO_NOT_TRACK=1 in advance.

    -a, --auto-update           Enable auto update feature of Coolify.

    -w, --white-labeled         Install white-labeled version.
    # Contact me before using it: https://docs.coollabs.io/contact

    -i, --white-labeled-logo    Custom logo for white-labeled.
    # Should be a http/https URL.
```

## Change Configuration

You can always execute the installation script with different options to
reconfigure Coolify.

For example:

- If you want to opt-out of tracking, execute the install script with
  `--do-not-track`.
- If you want to use the white-labeled version, execute the install script with
  `--white-labeled`.

:::warning
Some configurations are not preserved if you would like to change them on an already configured instance.

These options are the following: `--white-labeled`, `--do-no-track`, `--white-labeled-icon`.

So if you installed Coolify with `--do-no-track` before, and you want to also use `--white-labeled` option, you need execute the install script with `--do-not-track` and `--white-labeled`!
:::

## Restart

If for some reason, your instance crashes, you can restart it with the following command:

```bash
wget -q https://get.coollabs.io/coolify/install.sh \
-O install.sh; sudo bash ./install.sh -r
```

## Uninstall

You can easily uninstall Coolify by stopping the following containers,
`coolify`, `coolify-proxy` and `coolify-fluentbit`, or execute the following
script:

```bash
docker stop -t 0 coolify coolify-proxy coolify-fluentbit; docker rm coolify coolify-proxy coolify-fluentbit
```
