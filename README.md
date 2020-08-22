# Streamcamel System Administration Scripts

## Do Not add as a Submodule into Other Repositories

This repository is intended to carry sensitive information regarding system admin and credentials for
database access. Its use should be limited primarily to internal deployment.

## System/User Deployment Process

Using an administrator account, clone this repo:

```
git clone https://github.com/streamcamel/sysadmin
```

### To create new users

(insert here from old scratcher wiki)

## Scratcher Service Deployemnt Process

Clone this repo using appropriate scratcher account, such as `sc_streams` or `sc_nightly`:
_(do not use administrator account for service deployment)_

```
git clone https://github.com/streamcamel/sysadmin
```

Run the deploy script with the correct parameters for the user service responsibility:
```
# for user configured via scratcher_creds.ini:
~/sysadmin/deploy --autoslot

# ad-hoc task specification for unconfigured user:
~/sysadmin/deploy --autoslot --task='10min'
~/sysadmin/deploy --autoslot --task='nightly'
```

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
