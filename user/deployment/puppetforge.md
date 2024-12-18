---
title: Puppet Forge Deployment
layout: en
deploy: v1

---



Travis CI can automatically deploy your modules to [Puppet Forge ](https://forge.puppet.com/) or to your own Forge instance after a successful build.

To deploy to Puppet Forge, add your Puppet Forge username and your
[encrypted](/user/encryption-keys/#usage) Puppet Forge password to your
`.travis.yml`:

```yaml
deploy:
  provider: puppetforge
  user: "<Your username>"
  password:
    secure: "YOUR ENCRYPTED PASSWORD"
```
{: data-file=".travis.yml"}

## Deploy to a Custom Forge

To deploy to your own hosted Forge instance by adding it in the `url` key:

You can explicitly set the name via the **app** option:

```yaml
deploy:
  provider: puppetforge
  user: "<Your username>"
  password:
    secure: "YOUR ENCRYPTED PASSWORD"
  url: https://forgeapi.example.com/
```
{: data-file=".travis.yml"}

## Run Commands Before or After Deploy

Sometimes, you want to run commands before or after deploying. You can use
the `before_deploy` and `after_deploy` stages for this. These will only be
triggered if Travis CI is actually deploying.

```yaml
before_deploy: "echo 'ready?'"
deploy:
  ..
after_deploy:
  - ./after_deploy_1.sh
  - ./after_deploy_2.sh
```
{: data-file=".travis.yml"}
