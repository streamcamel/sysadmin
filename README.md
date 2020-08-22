# Streamcamel System Administration Scripts

## Do Not add as a Submodule into Other Repositories

This repository is intended to carry sensitive information regarding system admin and credentials for
database access. Its use should be limited primarily to internal deployment.

## Credentials Safety

This repository is safe for credentials storage since it does not need to be cloned onto Build & Test
(CI) infrastructure and its user-access can be restricted to a subset of individuals.

### Recommended Deployment Strategy for Credentials

Credentials stored in this repository are *not* intended for direct use by scratcher scripts. They
intended for use during deployment: 

 - initializing service accounts on servers
 - setting up secrets storage on AWS/GitHub

For example:
 - Deployment into GitHub Actions can be done via GitHub Secrets
 - Deployment onto servers can be done using Amazon Secrets or `ssh` infrastructure to deploy
   credentials into user accounts.
