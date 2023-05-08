---
head:
  - - meta
    - name: description
      content: Coolify - Applications
  - - meta
    - name: keywords
      content: applications coollabs coolify
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
      content: https://cdn.coollabs.io/assets/coollabs/og-image-applications.png
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
      content: https://cdn.coollabs.io/assets/coollabs/og-image-applications.png
---

# Applications

Applications are used to deploy a production version of your code. All data are based on your provided git repositories.

Coolify not just builds but also configures a reverse proxy (Traefik) automatically and requests an SSL certificate through Let's Encrypt.

You just need to push your code!

If you have a new build pack you would like to add, raise an idea [here](https://feedback.coolify.io/) to get feedback from the community!

## Supported Applications

Applications are based on `custom build packs` and `Heroku build packs`

Build packs have predefined configurations and build processes, especially for frameworks, like VueJs, Svelte, React, etc.

> These build processes do not handle all the use-cases, just the most commonly used ones. Consider using the `Docker` build pack if you need a custom build process.

- [Heroku](./heroku)
- [Static sites](./static)
- [NodeJS](./nodejs)
- [VueJS](./vuejs)
- [NuxtJS](./nuxtjs)
- [NextJS](./nextjs)
- [React/Preact](./react-preact)
- [Gatsby](./gatsby)
- [Svelte](./svelte)
- [PHP](./php)
- [Python](./python)
- [Laravel](./laravel)
- [Rust](./rust)
- [Docker](./docker)
- [Docker-Compose (beta)](./docker-compose)
- [Deno](./deno)

To choose the best-fitting build pack, Coolify scans your repository to guess it.

## Build Images

You can choose which build and deployment image you would like to use during build. For example node version 14/16/18.

## Secrets

Secrets are environment variables that should be set during build or runtime.

## Exposed Port

You can expose your application to a port on the host system.

> Useful if you would like to use your own reverse proxy or tunnel and also in development mode of Coolify.

## Automatic Deployment

Enable automatic deployment through webhooks. Enabled by default.

> Useful to turn off if you would like to deploy your applications manually, not on every commit.

## MR/PR Previews

Automatically builds `Merge Request` and `Pull Requests`. Default: `off`

> Useful when you would like to see others' work deployed.

They could have different `secrets` than the main application.

> Useful when you want to have a staging version of your application, e.g., connected to a separate database than the main application.

## Debug Logs

To see extended build logs. Default: `off`

> Useful if something is wrong with the build process.

## Deployment Types

### Integrated with Git App

Your application will be deployed through your Git App. Useful for private repositories.

> Fully integrated with Git flows, receive webhooks, rebuilds every commit, review PR/MR's, etc.

### Public Repository from Git

Your application will be built and deployed based on any public repositories from Github.com and Gitlab.com.

> No auto deployments based on new commits.

Examples:

- https://github.com/coollabsio/coolify-examples -> You can choose the branch.
- https://github.com/coollabsio/coolify-examples/tree/nodejs-fastify -> NodeJS & Fastify.
- https://github.com/coollabsio/coolify-examples/tree/compose -> Docker Compose
- https://github.com/coollabsio/coolify-examples/tree/react-vite -> React & Vite
- https://github.com/coollabsio/coolify-examples/tree/static -> Static

### Simple Dockerfile

Your application will be deployed based on the simple dockerfile you used.

> No Git integration, no need for a repository, just a pure Dockerfile.
