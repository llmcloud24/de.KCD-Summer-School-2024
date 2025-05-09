## Day 4: Certification

### Nginx Proxy Manager Showcase

> [!IMPORTANT]
> Unfortunately, due to practicality and time constraints, we will not do an in-depth hands-on session for this.
> 
> We recommend that you focus on the live showcase instead.
> 
> This example will still work, if you have more control over your infrastructure, and know what you're doing.
>
> Feel free to try and deploy it and see if you can access the interface, but do anticipate that things might not work properly.

### What is Nginx Proxy Manager (NPM)?

* Nginx Proxy Manager is a simple tool that helps manage how web traffic is directed (reverse proxy).
* It allows you to control where users go when they visit different websites or services on your server (domain management, URL forwarding).
* You can secure your site with HTTPS (SSL certificates) easily.
* Instead of using complex commands (Nginx configuration), it offers a user-friendly interface to set everything up with just a few clicks.
* Imagine it as a GUI-friendly Nginx with the caveat of being slightly less flexible.


### How is it useful here?

* We use it to assign a nice URL for your VM (and port), e.g.: `10.0.2.10:80 --> foo-vm.llmcloud24.bihealth.org`
* In this session, we all get some cute animals, e.g., `https://okapi.llmcloud24.bihealth.org`
* With this, your web service or app is exposed to the outside world and can be visited externally. No need for SOCKS proxy yay!
* We also use this to secure these URLs and make them HTTPS with our SSL certificates 


### How can you deploy it?

* If you cloned our Summer School repository, you can `cd` into the `Day_4/03-Certification` folder
* Then run `docker compose up --build` and it should work out of the box
* If you visit <your VM's FLOATING IP> in your browser with the SOCKS proxy, you will see a page indicating that Nginx Proxy Manager is installed and running.
* You can also access the web page in your browser with the SOCKS proxy at `<your VM's FLOATING IP>:81` with the user `admin@example.com` and password `changeme`. This page is not exposed and is only accessible from your VM's floating IP.
* If your SOCKS proxy or browser does not work, you can also try to do `curl localhost:80` or `curl localhost:81` and look for the mentions related to Nginx Proxy Manager just to get confirmation that you did everything correctly.
