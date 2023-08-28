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

Servers are where all your resources are deployed to. It could be a local server (where Coolify is installed) or any remote server.

### Requirements

- SSH connectivity between Coolify and the server.
- SSH key for authentication.

### Actions taken by Coolify

Coolify will automate a few maintenance (system administrator) tasks on the operating system and monitors its resources.

You will get notified via the notification system you set(webhook, email, discord, slack, telegram).

## Project

Resources are grouped together into a project, a tree structure. A project could have infinite number of resources.

<iframe src="https://link.excalidraw.com/readonly/DDJvzrOunjuYdYGtBqF6" width="100%" height="500px" style="border: none;"></iframe>

## Environment

Each project, by default have a `production` environment, that is not deletable, but renameable.
Environments consists of resources, like [application](#application), [database](#database) or a [service](#service), etc.

## Application

An application could be a web application, a static website, a backend API, etc. It is a container that runs a process deployed to a defined [server](#server).

## Database

A database is a container that runs a database process deployed to a defined [server](#server).

## Service

A service is a more complex type of resource, that consists of several other resources, like an [application](#application) and a [database](#database), etc.

Imagine you would like to deploy a Wordpress application, you would need a database, a web server and a PHP runtime. You could create a service that consists of these resources, grouped together and created automatically for you. Each resource in a service could be deployed to a different server.

## Proxy
A server could have a proxy that is used to route traffic to the right resource. It is not mandatory, but it is highly recommended to use a proxy. By default you will have to set up your own proxy to allow domains to access your Coolify applications, of which each is stored in ther own docker container.

To use Coolify's built-in proxy which is built on top of Traefik, in the dashboards page, under the "Destinations" category, click on a destination such as "Local Docker" and enable the setting "Use Coolify Proxy?" and click save. Do not click "Force restart proxy" as that will reset the setting you just enabled.

## Destination
Destination defines the type of the containerization technology you would like to use. It could be Docker, Docker Swarm or Kubernetes.

## Source
Source defines the type of the source code repository you would like to use, like Github, Gitlab, Bitbucket, etc.
