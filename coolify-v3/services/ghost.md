---
head:
  - - meta
    - name: description
      content: Coolify - Services - Ghost
  - - meta
    - name: keywords
      content: services ghost coollabs coolify 
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
# Ghost
Based on [Ghost](https://github.com/TryGhost/Ghost).

Ghost is a free and open-source content management system (CMS) and blogging platform. Spin up a Ghost instance within minutes using the Ghost service within Coolify!

## Get started

Follow the steps below to setup a Ghost instance:

1. From Coolify dashboard, select "+ Create New Resource".
2. Choose "Service"
3. Select "Ghose (MySQL)" 
4. In the Configurations tab, type out the URL for the Ghost instance (Setup DNS records before deploying)
5. Click "Save" and then click "Deploy" to start the service
6. Your new Ghost instance will be live within a few minutes!

## Access Ghost and set it up

Once the Ghost instance is up and running, follow the steps to set up a user:

1. Access the Ghost blog by navigating to the URL which you specified in the Configuration
2. To setup an administrator user, navigate to https://YOUR_GHOST_URL/ghost (ex. https://www.example.com/ghost) and follow the steps

## Set up email for Ghost

You can set up email service for Ghost by using enviroment variables. Specify the following enviroment variables inside the service's Secrets tab within Coolify:

1. mail__options__from - Specify the from email address (If you receive an error when sending emails, try changing mail__options__from to mail__from instead)
2. mail__transport - Preferably SMTP 
3. mail__options__host - The SMTP host url, get this from your mail provider
4. mail__options__port - The SMTP port to use, get this from your mail provider
5. mail__options__secureConnection - true if using HTTPS
6. mail__options__auth__user - SMTP username, get this from your mail provider
7. mail__options__auth__pass - Password for the SMTP username, get this from your mail provider

Save the secrets and redeploy your Ghost instance. You should now be able to send emails using Ghost!

### For more information, please checkout

- [Ghost Docs](https://ghost.org/docs/)
- [Ghost Docs env vars](https://ghost.org/docs/config/)
