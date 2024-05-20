# certbot_cloudflare Ansible Role

## Overview

The `certbot_cloudflare` role automates the process of obtaining and renewing SSL certificates from Let's Encrypt using the Cloudflare DNS challenge. This role configures Certbot with the necessary Cloudflare credentials and sets up Nginx with the SSL configuration.

## Requirements

- Ansible 2.9 or higher
- An Nginx server installed on the target hosts
- Cloudflare account with API token that has DNS edit permissions

## Role Variables

The following variables can be defined in `defaults/main.yml` or overridden in your playbook:

```yaml
# Cloudflare API token
cloudflare_api_token: "your_cloudflare_api_token"

# Email address for Let's Encrypt notifications
letsencrypt_email: "your_email@example.com"

# Domain for which the SSL certificate will be obtained
letsencrypt_domain: "yourdomain.com"

# Path to the Nginx SSL configuration template
nginx_ssl_template: "options-ssl-nginx.conf.j2"
```

## Example Playbook

Below is an example playbook that uses the `certbot_cloudflare` role:

```yaml
- hosts: webservers
  become: true
  vars:
    cloudflare_api_token: "your_cloudflare_api_token"
    letsencrypt_email: "your_email@example.com"
    letsencrypt_domain: "yourdomain.com"
  roles:
    - certbot_cloudflare
```

## Template

The role includes a Jinja2 template for the Nginx SSL configuration:

- `templates/options-ssl-nginx.conf.j2`: This template sets up SSL options for Nginx to use the certificates obtained by Certbot.

## License

This role is licensed under the MIT License.

## Author Information

This role was created by Gizex.
