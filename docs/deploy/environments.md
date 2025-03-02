---
seotitle: Environments – Creating local, preview, and prod environments
seodesc: Learn how to create all the environments you need for your backend application, local, preview, testing and production. Here's how you keep them in sync!
title: Environments
subtitle: The environments you want, with none of the work
---

Encore makes it simple to create the environments you need to build your application with confidence: local, preview, testing, and production.
Each environment is an isolated fully working instance of your backend, automatically provisioned by Encore.

Environments always stay in sync, as they are created based on the needs of your application, using the [Encore Application Model](/docs/introduction#meet-the-encore-application-model). Environments are provisioned using contextually appropriate [infrastructure](/docs/deploy/infra) depending on the type of environment.

## Creating environments

To create an environment for your app, open your app in the [Cloud Dashboard](https://app.encore.dev) and go to the **Environments** page,
then click on `Create env` in the top right.

There you can pick a name, and decide if you want a production
or development environment (see [Environment Types](#environment-types) below).

Choose how you would like to deploy to the environment (either by pushing
to a Git branch or manually triggered), and whether or not you want to manually approve infrastructure provisioning or simply let Encore handle it.

Finally, select which cloud provider you want to deploy to (see the [Cloud Providers](/docs/deploy/own-cloud) documentation to learn more),
and click `Create`. That's it!

![Creating an environment](/assets/docs/createenv.png "Creating an environment")

## Environment Types

Encore has two primary types of environments: `Production` and `Development`.

`Development` environments include local, preview, and all environments created with the `Development` type.


They differ in the type of infrastructure that is provisioned:
- Production environments are provisioned for maximum reliability, availability, and scalability.
- Development environments are optimized to be cost-efficient and fast to provision.

Learn more about how different environments are provisioned in the [infrastructure documentation](/docs/deploy/infra).

Aside from determining infrastructure, environment type is also used for [Secrets management](/docs/develop/secrets).

## Local environment

When you've installed the [Encore CLI](/docs/install), you start your local environment by simply running `encore run`.
This builds and tests your application, and provisions all the necessary infrastructure to run your application locally (see the [infra docs](/docs/deploy/infra#local-development) to learn exactly how local infrastructure is provisioned).

By default, the local environment runs on `http://localhost:4000`.

## Preview environments

When you [connect your application to GitHub](/docs/how-to/github), Encore will automatically provision ephemeral Preview Environments for each Pull Request. See the [Preview Environments documentation](/docs/deploy/preview-environments) to learn more.

### Frontend Collaboration

Preview Environments make it really easy to collaborate and test changes with your frontend.
Just update your frontend API client to point to the `pr:#` environment.
This is a one-line change since your API client always specifies the environment name, e.g. `https://<env>-<my-app>.encr.app/`.

If your pull request makes changes to the API, you can [generate a new API client](/docs/develop/client-generation)
for the new backend API using `encore gen client --env=pr:72 --lang=typescript my-app`

## Cloud environments

Encore makes it simple to create multiple cloud environments using different cloud providers, by [connecting your cloud account](/docs/deploy/own-cloud). Cloud environments can be created as `Development`, or `Production`, depending on your use case (see the [infra docs](/docs/deploy/infra#production-infrastructure) to learn exactly what infrastructure is provisioned in each cloud).