# Example static website with Docker, Nginx and Certbot

This is full project structure example of article [**How to dockerize your static website with Nginx, automatic renew SSL for domain by Certbot and deploy it to DigitalOcean?**](https://dev.to/koddr/how-to-dockerize-your-static-website-with-nginx-automatic-renew-ssl-for-domain-by-certbot-and-deploy-it-to-digitalocean-4cjc)

Published on [Dev.to](https://dev.to/koddr/how-to-dockerize-your-static-website-with-nginx-automatic-renew-ssl-for-domain-by-certbot-and-deploy-it-to-digitalocean-4cjc) @ 27 Jan 2020.

## Requirements

- Docker `19.x+`

## Usage

- Change `site.com` with your website name on docker-compose.yml environment variable.
- docker-compose.client.yml is not used! Just as example of docker-compose to be added on other apps/monorepo.
- Push configured project to your own git repository.
- Go to [DigitalOcean](https://m.do.co/c/b41859fa9b6e) account, create and configure new droplet (see screenshots in [article](https://dev.to/koddr/how-to-dockerize-your-static-website-with-nginx-automatic-renew-ssl-for-domain-by-certbot-and-deploy-it-to-digitalocean-4cjc)).
- Connect via SSH to your droplet and `git clone` your repo.
- Check configuration of `Certbot`, start the process of obtaining SSL certificate in test mode:

```console
make certbot-test DOMAINS="site.com www.site.com" EMAIL=mail@site.com
```

- If you see `Congratulations!`, all okay; start the process of obtaining SSL in production mode:

```console
make certbot-prod DOMAINS="site.com www.site.com" EMAIL=mail@site.com
```

- And now, check Nginx config:

```console
make deploy-test
```

- No errors? Go your static website to production:

```console
make deploy-prod
```

- That's all!
