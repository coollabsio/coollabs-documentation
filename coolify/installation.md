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

Installation is automated with a single script.

```bash
curl -fsSL https://cdn.coollabs.io/coolify/install.sh | bash
```

You can find the source code [here](https://github.com/coollabsio/coolify/blob/main/scripts/install.sh).

The script will do the following on your operating system:
- Basic commands: `curl wget git jq jc`
- Docker Engine (23+)
- Configures proper logging for Docker Engine.
- Creates directory structure at `/data/coolify` for all the configuration files.
- Creates an SSH key for Coolify to be able to manage this server from itself at `/data/coolify/ssh/keys/id.root@host.docker.internal`.
- Install dockerized Coolify.

## Requirements

### Supported Architectures

`AMD64` and `ARM` architecture are supported.

### Supported Operating Systems

`Debian` based servers are supported, due to the installation script (Coolify
itself supports every OS that could run a Docker Engine). If you would like to
have other, please consider
[open an issue on GitHub](https://github.com/coollabsio/coolify/issues/new).

### Resources

Minimum required resources for Coolify:

- 2 CPUs
- 2 GBs memory
- 30+ GB of storage for the images.

### Additional Resources

Based on what you would like to run with Coolify, additional resources (CPU, memory, disk) are needed.

Self-hosting could be heavy if you would like to run a lot of things.

For example, I'm hosting most of my production stuffs on a server with:

- 8GB of memory (average usage 3.5GB)
- 4 CPUs (average usage ~20-30%)
- 150GB disk (usage 40GB)

Hosting the following things:

- 3 NodeJS apps
- 4 Static sites
- Plausible Analytics (for visitor analytics)
- Fider (feedback tool)
- UptimeKuma (uptime monitoring)
- Ghost (my newsletters)
- 3 Redis databases
- 2 PostgreSQL databases


## Uninstall

You can easily uninstall Coolify by stopping the following containers,
`coolify`,`coolify-db`, `coolify-proxy`, and `coolify-redis` or by executing the following script:

```bash
docker stop -t 0 coolify coolify-db coolify-proxy coolify-redis; docker rm coolify coolify-db coolify-proxy coolify-redis
```

You also need to cleanup all the docker volumes as well.

```bash
docker volume rm coolify-db coolify-redis
```

:::warning

The following command will delete EVERYTHING related to your configurations, backups, etc.

:::

And delete all configurations in `/data/coolify`:

```bash
rm -f /data/coolify
```