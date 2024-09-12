# What needs to be changed/done:

- - [ ] Remove our own LLM + GUI deployment
- - [ ] Adapt our compose files to work with Day 3's

## what we have/need:

- - [x] an nginx-proxy-manager vm that's connected to the loadbalancer
  - [x] create/using certs (idea: certbot to generate, add via npm gui?)
  - [ ] Jakob WIP: setting up infrastructure for certification
  - [x] uptime monitoring (idea: show an upptime example of anything, like google.com etc, just to show the possibility)
  - [x] show backup things: rsync, nfs share, cronjob (idea: set up nfs, mount it, setup a cronjob to rsync a folder)
  - [x] adding an auth layer/image (oauth2-proxy or something) on top of their existing apps from Day 3 (wip: depends on whether we can get it working on Day 3's setup?)
  - [x] show/make them do things via github repo (idea: make them pull the scripts/templates from there, and make them commit their stuff as we go through the course?)
