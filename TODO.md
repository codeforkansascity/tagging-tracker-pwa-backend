### Create instructions for deployment to EC2 with automatic cert with cert bot

### Deployment
- [ ] make it easier/better

### Node
- [ ] handle case where no `AWS` credentials can break server
- [ ] check any `Throw error()` calls, these break `Node`

### Database
- [ ] make sure table seeding works from scratch
- [ ] update migrations(lack of) some tables changed in schema, some of the seed definitions are now rong eg. `tags` table

### Extra
- [ ] determine max connection limit for MySQL based on RAM/buffer/etc calculations
- [ ] image downsizing on remote side eg. with `jimp` this isn't really needed as the client resizes the images/displays using thumbnails