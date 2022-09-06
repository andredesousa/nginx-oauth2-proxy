# OAuth2 Proxy with Nginx

This project shows how to use [OAuth2 Proxy](https://oauth2-proxy.github.io/oauth2-proxy/), [GitHub OAuth Apps](https://github.com/settings/developers) and [Nginx](https://www.nginx.com/) to route traffic.

## Overview

Many application do not provide built-in authentication or access control out-of-the-box.
Due to the sensitive data these applications process, this can be a major problem and it is often necessary to provide some type of security.

[OAuth2 Proxy](https://oauth2-proxy.github.io/oauth2-proxy/) is a reverse proxy that sits in front of your application and handles the complexities of OpenID Connect/OAuth 2.0 for you.

<img src="https://developer.okta.com/assets-jekyll/blog/add-auth-to-any-app-with-oauth2-proxy/oauth2-proxy-diagram-09c03e3355965bf4d0f8d26911206e015d448b8802f86237a8a17701c173d04e.jpg" width=35% height=35%>

OAuth2 Proxy provides authentication using providers (GitHub, Google, and others) to validate accounts by email, domain or group.

## Prerequisites

Follow the next instructions to configure and run the project on your local machine:

- Install [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/).
- Register a new *GitHub App* to allow the access to *GitHub OAuth Apps*.
- Provide the following environment variables for Docker Compose:
  - `OAUTH2_PROXY_CLIENT_ID`
  - `OAUTH2_PROXY_CLIENT_SECRET`
  - `OAUTH2_PROXY_COOKIE_SECRET`

## GitHub OAuth Apps

Before you begin, you’ll need a free GitHub developer account.
Go to <https://github.com/settings/developers> and register a new OAuth application.

## Deploying

To start the application, you can use the next command:

```bash
docker-compose up
```

It will start a sample `web-app`, `oauth2-proxy` and `nginx` services.
Then go to <http://localhost/> and you’ll be redirected to GitHub.

If you have an `.env` file, you can use `docker-compose --env-file .env up` command.

## References

For further reference, please consider the following articles:

- [OAuth2 Proxy Docs](https://oauth2-proxy.github.io/oauth2-proxy/docs/)
- [Add Auth to any App with OAuth2 Proxy](https://developer.okta.com/blog/2022/07/14/add-auth-to-any-app-with-oauth2-proxy#is-oauth2-proxy-right-for-your-application)
- [Securing application access with Ingress, OAuth2, and GitLab](https://oak-tree.tech/blog/k8s-nginx-oauth2-gitlab)
- [Using environment variables and files with Docker Compose](https://towardsdatascience.com/a-complete-guide-to-using-environment-variables-and-files-with-docker-and-compose-4549c21dc6af)
