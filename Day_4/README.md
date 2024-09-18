# Day 4 - How to Service – Ensuring Continuous Support throughout Operations

Table of Contents:

- [Background](#background)
- [Certification](#certification)
- [Authentication](#authentication)
- [Monitoring](#monitoring)
- [Backups](#backups)
- [SOCKS proxy](#socks-proxy)

## Background

Ensuring continuous support throughout operations is crucial for maintaining the reliability, security, and efficiency of any system or service. This session we will discuss the key components that underpin robust operational support, including certification, authentication, monitoring, and backups. By understanding and implementing these elements effectively, organizations can minimize downtime, protect sensitive data, and provide seamless experiences for users.

## 1 General Project Setup

An overview of the planned project setup

![alt text](images/llmcloud24.png)


## Deploying ollama with docker setup

How to run a model now inside the container e.g.

```
docker exec -it ollama ollama run llama2
```

## 2 Monitoring

Ongoing monitoring of system and application performance, security, and infrastructure health enables early issue detection and swift resolution.

## 3 Backups

Regular, secure backups following strategies to ensure that data can be restored after loss or corruption, maintaining operation continuity. Implementing automated backup solutions and storing backups in multiple locations safeguards against various failure scenarios and minimizes downtime.

## 4 Certification
Implementing TLS (Transport Layer Security) certificates to secure data transmission ensures encrypted communication between clients and servers, protecting sensitive information from interception and tampering.

## 5 Authentication

Integrating robust authentication methods to prevent unauthorized access and enhance security to ensure that only authorized users can access critical systems and data.

![alt text](images/Github-Oauth.png)


## How to access internal Network with Socks Proxy

A SOCKS proxy (Socket Secure) is an internet protocol that routes network traffic between a client and a server via a proxy server. Unlike traditional proxies, SOCKS operates at the transport layer, handling any type of traffic, such as HTTP, FTP, and SMTP. It offers more flexibility, as it doesn’t interpret or modify network traffic, making it suitable for a wide range of applications, including web browsing, file transfers, and peer-to-peer networks. SOCKS5, the latest version, adds support for authentication and UDP traffic, improving security and performance for various use cases.

### Introduction

In our case we use a SOCKS5 proxy to reach an internal network. The connection to the internal netwok can then be used by the browser to show web pages that are not reacheable from the internet but only from inside the de.NBI cloud. 

### Setup

The proxy server in this case is created on the local machine or 'localhost'. To establish the SOCKS5 proxy a ssh connection with a specific port is created. To use the connection the browser proxy settings must be changed to use 'localhost' on the port defined in the ssh connection as a SOCKS5 proxy. Now the browser (client) can connect to the server in the de.NBI cloud.

### SSH config

```config
Host de.NBI-socks-proxy
    HostName denbi-jumphost-01.bihealth.org
    User jakobmathis
    IdentityFile ~/.ssh/privkey.key
    DynamicForward 127.0.0.1:4321
    ServerAliveInterval 120
```

Entry in the ssh config.

### Browser settings

The easiest way to setup the proxy in the browser is by changing the browser settings.

![Browser proxy settings](images/browser-socks-proxy.png)

You can also add an extension like the "Proxy Switcher and Manager" to the browser. This extension should work with [chrome](https://chromewebstore.google.com/detail/proxy-switcher-and-manage/onnfghpihccifgojkpnnncpagjcdbjod), [edge](https://microsoftedge.microsoft.com/addons/detail/proxy-switcher-and-manage/gneeeeckemnjlgopgpchamgmfpkglgaj) and [firefox](https://addons.mozilla.org/en-US/firefox/addon/proxy-switcher-and-manager/).

![browser extension](images/proxy_browser_extension.png)

With the extension installed you can setup multiple configurations for each connection you want to have and change the proxy settings by clicking on the correct tab. The default tab is 'System Proxy', when selected the browser will use the global proxy settings from the operating system. The tab for using the SOCKS proxy is 'Manual Proxy'.
Give the ip address of localhos 127.0.0.1 and fill in the port of the ssh connection, 4321. Select 'SOCKS v5' as 'Server Type'. Give the connection a recognizable name and save it by clicking on the green checkmark.

![browser extenion setup](images/proxy_browser_extension_setup.png)
