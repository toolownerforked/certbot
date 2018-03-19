# certbot

Get and renew Let's Encrypt Wildcard Certificates using Certbot.

## `runme.sh`

| Command   | Description                                      |
| --------- | ------------------------------------------------ |
| -get      | get LE's wildcard certficicates for `--host`     |
| -renew    | renew all existing expiring certificates         |
| -revoke   | revoke `--host` certificate                      |
| -clean    | remove all certificates                          |
| -test     | use staging test server instead of production    |


| Option    | Description                                      |
| --------- | ------------------------------------------------ |
| --host    | FQN of the host to get the wildcard certificate  |
| --email   | email for updates and expiry                     |
| --dns     | dns-01 validation service                        |

### `-get`

Get new wildcard certificates including root.

Example:

    runme.sh -get --host example.com --email certs@example.com --dns google

`example.com` is the target to get Let's Encrypt certificate for.
Both `*.example.com` and `example.com` certificates are ordered.
`certs@example.com` is your email address required by LE.

### `-renew`

Renews all certificates that are expiring.

### `-test`

Optional flag for getting certificates from staging server instead of production.

### `-revoke`

Revoke a certificate.

### `-clean`

Removes the `letsencrypt` directory. Use it with caution after test runs only.

### `--dns`

Domain validation services. Currently supporting ony `google` and `digitalocean`.

-------------------------------------------------------------------------------

# Usage Instruction

## Get Let's Encrypt Wildcard Certificate

    docker run --rm -t -v <local-dir>:/data \
        aquaron/certbot certbot --email <email> --host <fqn> --dns <dns-01> -[get|revoke|renew] [-test]

