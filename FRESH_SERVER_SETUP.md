### General
This should primarily just be installing deps, cloning a repo, updating config, seeding db, etc... to get it working.
I'm going to figure out an NGINX setup with Let's Encrypt so it's self-updating SSL wise, should have done that in the past haven't put the time in.
Will log any problems I run into.

I'm using a Debian 10 VPS from OVH, it's the smallest one eg. single core 2GB RAM 20GB SSD for $3.50/mo or less if bought in bulk

Just changed password on the box from default

- have domain, point to server ip
  - if using subdomain like api.domain.com use an A record, host is api
- setup SSL ([NGINX with Let's Encrypt](https://www.howtoforge.com/tutorial/nginx-with-letsencrypt-ciphersuite/))
- install Node 14/npm
- install git, add creds to pull this repo
- update ssl file paths
- setup db and update env file
- run repo with pm2

#### NGINX Let's Encrypt setup
- before running the `certbot certonly...` step make sure the api.domain.com resolves with non-https to the default NGINX welcome page
  - then change the url at the end eg. don't use hakase-labs.io use api.domain.com
  - skipping dhparam 4096, takes way too long on this dinky VPS, can generate elsewhere and move in but yeah
  - nope can't skip it, will generate it on a stronger computer so it takes less time and sftp it in
  - made the file, moved it over to `/etc/nginx` was able to restart server have ssl
  - at this point have an SSL enabled site hopefully A or A+ rating in Qualys SSL Labs
  - note about not using TLS 1/1.1

#### Getting code to run
- install deps
  - [node/npm](https://github.com/nodesource/distributions/blob/master/README.md)
  - [mysql/mariadb](https://www.digitalocean.com/community/tutorials/how-to-install-the-latest-mysql-on-debian-10)
    - seed it with node script (need to add env config for mysql client)
      - had problems with dotenv, had to set path like this:
        `require('dotenv').config({path:__dirname+'/./../../.env'});`
    - create users by running method that runs bcrypt hashing on plain text passwords
- clone repo, npm install
- fill out rest of env like AWS related
- do AWS config
- run app with pm2
- test
  - login
  - sync down
  - sync up
  - images make it to AWS S3