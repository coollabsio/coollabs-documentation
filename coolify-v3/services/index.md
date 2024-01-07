---
head:
  - - meta
    - name: description
      content: Coolify - Services
  - - meta
    - name: keywords
      content: services coollabs coolify 
  - - meta
    - name: twitter:card
      content: summary_large_image
  - - meta
    - name: twitter:site
      content: '@heyandras'
  - - meta
    - name: twitter:title
      content: Coolify
  - - meta
    - name: twitter:description
      content: An open-source & self-hostable Heroku / Netlify alternative.
  - - meta
    - name: twitter:image
      content: https://cdn.coollabs.io/assets/coollabs/og-image-services.png
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
      content: https://cdn.coollabs.io/assets/coollabs/og-image-services.png
---
# Services

Services are popular open-sourced and self-hostable applications provided as a service for you.

If you have a new service you would like to add, raise an idea [here](https://github.com/orgs/coollabsio/discussions) to get feedback from the community or submit a [service template](https://github.com/coollabsio/coolify-community-templates)!

## Supported Services

- [WordPress](https://wordpress.org)
- [Ghost](https://ghost.org)
- [Plausible Analytics](https://plausible.io)
- [NocoDB](https://nocodb.com)
- [VSCode Server](https://github.com/cdr/code-server)
- [MinIO](https://min.io)
- [VaultWarden](https://github.com/dani-garcia/vaultwarden)
- [LanguageTool](https://languagetool.org)
- [n8n](https://n8n.io)
- [Uptime Kuma](https://github.com/louislam/uptime-kuma)
- [MeiliSearch](https://github.com/meilisearch/meilisearch)
- [Umami](https://github.com/mikecao/umami)
- [Fider](https://fider.io)
- [Hasura](https://hasura.io)
- [Appwrite](https://appwrite.io)
- [Glitchtip](https://glitchtip.com)

:::warning
Some applications could take several minutes to start up. Please wait a bit after you start.
:::

## Requirements
Each service requires a specific amount of `CPU / memory / storage`. See their documentation to help on how to choose your hardware details.

## Exposed Port
You can expose your application to a port on the host system.

> Useful if you would like to use your own reverse proxy or tunnel and also in development mode of Coolify. 

## Persistency
All data are persistent. That means, if you stop a service, all your data persist on a Docker Volume. If you stop/start a service, you will keep your data as-is.

## Logs
You can check the runtime logs of your services.

## Secrets
There are some predefined secrets on the frontend, that are generated automatically (like passwords, users.) or you can fill manually. If you need any further environment variable, you can define them in the secrets tab.

## Update Versions
If you stop/start a service, the latest docker image will be pulled for the selected image tag.
