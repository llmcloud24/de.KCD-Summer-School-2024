# What needs to be changed/done:

- - [ ] Remove our own LLM + GUI deployment
- - [ ] Adapt our compose files to work with Day 3's

## what we have/need:

- - [x] an nginx-proxy-manager vm that's connected to the loadbalancer
  - [x] create/using certs (certbot, or..?)
  - [x] show an upptime example (of anything, like google.com etc)
  - [x] show backup things: rsync, nfs share, cronjob
  - [x] adding an auth layer/image (oauth2-proxy or something) on top of their existing apps from Day 3 (requires validation)
  - [x] show/make them do things via github repo
