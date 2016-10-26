## External authenticator for Certbot

This plugin helps with domain validation process by calling external 
program or by printing JSON for the

The plugin is designed mainly to automate DNS validation.

To install, first install let's encrypt (either on the root or in a virtualenv),
then:

```
python setup.py install
```

To use, try something like this:

```
certbot --agree-tos --email you@example.com \
        -a certbot-external-auth:out \
        --certbot-external-auth:out-public-ip-logging-ok \
        -d example.com certonly
```

This plugin only supports authentication, not installation.

Currently it produces one-line JSON with challenge to process by the script 
on the stdout. After the challenge is processed, external process is supposed
to send a new line to continue with the process.

## Example 

TBD.

## Future work

* Communicate challenges via named pipes
* Communicate challenges via sockets
* Call an external script with the challenges in parameter


## About

Loosely based on the Let's Encrypt nginx plugin and [certbot-external]

Once ticket [2782] is resolved this won't be needed. 

[certbot-external]: https://github.com/marcan/certbot-external
[2782]: https://github.com/certbot/certbot/issues/2782
