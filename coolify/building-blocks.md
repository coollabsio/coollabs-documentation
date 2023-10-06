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

# Building Blocks

## Server

Servers are where all your resources are deployed to. 

### Types
- **Localhost:** the server where Coolify is installed.
- **Remote Server:** could be any server, reachable through SSH.

### Requirements
#### Localhost
To be able to manage the server where Coolify is running on, the docker container of Coolify should reach the host server through SSH.

You can use localhost as a server where all your resources are running, but it is not recommended as high server usage could prevent to use Coolify.

:::tip
You can use our [Cloud](https://app.coolify.io) version, so you only need a server for your resources. You will get a few other things included with the cloud version, like free email notifications, s3 storage, etc based on your subscription plan.
:::

   
#### Remote Server
Its only purpose to host your resources, not Coolify itself.

You need the followings on the remote server:

1. Connectivity
   - SSH connectivity between Coolify and the server with SSH Key Authentication.
   :::tip
   Your public key should be added to **root** user's `~/.ssh/authorized_keys`.

   If you do not have an SSH Key, you can generate on through Coolify with a simple button or you can generate one manually.
   :::
   - Root user access.
2. Docker Engine (23+)
   - Automatically installed from the UI or you can install manually.

The only manual step you need to do is to place your SSH key on the server, into root user's `~/.ssh/authorized_keys` file.



### Automations & Monitoring

Coolify will automate a few maintenance tasks on the operating system, so you do not need to do them manually.

Coolify monitors your server & your deployed resources and immediately notifies you if something good or bad happens. You will always know what is going on in your self-hosted environment.

All you need to do is to setup your preferred notification system. Currently available:
- Email
- Discord Webhooks
- Telegram Bot

WIP:
- Webhooks
- Slack


## Project

Resources are grouped together into a project, a tree structure. A project could have infinite number of resources.

<iframe src="https://link.excalidraw.com/readonly/DDJvzrOunjuYdYGtBqF6" width="100%" height="500px" style="border: none;"></iframe>

## Environment

Each project, by default have a `production` environment, that is not deletable, but renameable.
Environments consists of resources, like [application](#application), [database](#database) or a [service](#service), etc.

## Application

An application could be a web application, a static website, a backend API, etc. It is a container that runs a process deployed to a defined [server](#server).

### Types
1. Public or Private Git repository
   - Private Git repositories could be deployed with a GitHub App, or with [Deploy Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys) 
2. Simple Dockerfile

To have full integration with GitHub, like fully automated commit or pull request based deployments, you need a GitHub App (created automatically by Coolify).


## Database

All supported databases could have scheduled, automatic backups, that is saved to your server or to an S3 compatible storage.

### Types
- PostgreSQL
:::tip
MySQL, MariaDB, MongoDB, etc, coming soon...
:::

## Service 

:::warning
Work in progress..,
:::

A service is a more complex type of resource, that consists of several other resources, like an [application](#application) and a [database](#database), etc.

Imagine you would like to deploy a Wordpress application, you would need a database, a web server and a PHP runtime. You could create a service that consists of these resources, grouped together and created automatically for you. Each resource in a service could be deployed to a different server.

## Proxy
A server could have a proxy that is used to route traffic to the right resource. It is not mandatory, but it is highly recommended to use a proxy.

Coolify uses Traefik at the moment. Configuration done automatically by Coolify in case you deploy a resource that requires this proxy.

Like if you add a domain to your application, Coolify detects it and starts a proxy automatically.

:::tip
Free SSL certificates included, thanks to Let's Encrypt.
:::

## Destination
Destination defines the type of the containerization technology you would like to use. It could be Docker, Docker Swarm or Kubernetes.

:::tip
Currently only standalone Docker engine is supported.
:::

## Source
Source defines the type of the source code repository you would like to use, like Github, Gitlab, Bitbucket, etc.

Github & GitLab public source is defined by default, but unseen by the users.

To use private repositories, you need to make a GitHub or GitLab App to have all kinds of integrations available.
