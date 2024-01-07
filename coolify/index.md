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

# Coolify

:::tip
This is the documentation of Coolify v4 beta. What you see here is not finished, could be changed overtime. 
:::

## What is Coolify?
Coolify is an all-in one PaaS that helps you to self-host your own applications, databases or services (like Wordpress, Plausible Analytics, Ghost) without managing your servers, also known as an open-source & self-hostable Heroku / Netlify alternative.

Looking for the hosted cloud & paid version? [Here you go.](https://app.coolify.io)

## Features
- **BYOS:** Bring your own server from any cloud providers, or even your own server at home! All you need is SSH access. You will have full control over your server, and you can even use it for other purposes.
- **Server Automations:** Once you connected your server, Coolify will start managing it and do a lot of administrative tasks for you. You can also write your own scripts to automate your server.
- **No Vendor Lock-in:** You own your own data. All configurations saved on your own servers, so if you decide to stop using Coolify, you can still continue to manage your deployed resources.
- **Monitoring:** Coolify will automatically monitor your configured servers and deployed resources. Notifies you if something goes wrong on your favourite channels, like Discord, Telegram, via Email and more.
- **Automatic Backups:** We automatically backup your databases to any S3 compatible solution. If something goes wrong, you can easily restore your data with a few clicks.
- **Powerful API:** Programmatically deploy, query, and manage your servers & resources. Integrate to your CI/CD pipelines, or build your own custom integrations. 
- **Push to Deploy:** Git integration is default today. We support hosted (github.com, gitlab.com) or self-hosted (Github Enterprise, Gitlab) Git repositories.
- **Pull request Deployments:** Automagically deploy new commits and pull requests separately to quickly review contributions and speed up your teamwork!

:::warning
Some features are work in progress and will be available soon.
:::

