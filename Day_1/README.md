# How to cloud

Our first day will give you an introduction to the setup of our OpenStack Cloud, so you are prepared to start a virtual machine and work on your own project.

1. Introduction to cloud portal: **https://cloud.denbi.de/portal**
  - further explanation of the cloud portal: https://cloud.denbi.de/wiki/portal/allocation/
2. Introduction to OpenStack cloud via de.NBI Cloud wiki: **https://cloud.denbi.de/wiki/quickstart**
  - A brief overview of the OpenStack concepts can be found here: https://cloud.denbi.de/wiki/Concept/basics/
  - A brief overview of the general OpenStack components can be found here: https://cloud.denbi.de/wiki/Concept/openstack/
3. Specific Information about de.NBI Cloud site in Berlin: **https://cloud.denbi.de/wiki/Compute_Center/Berlin**

[Slides for general introduction](https://github.com/llmcloud24/de.KCD-Summer-School-2024/blob/main/Day_1/deKCD_day1_project_intro.pdf)  
[Slides for technical introduction](https://github.com/llmcloud24/de.KCD-Summer-School-2024/blob/main/Day_1/deKCD_day1_technical_intro.pdf)

## Hands-on part

## 1. Join the LLMcloud24 project in de.NBI Cloud Berlin
- register via LifeScience AAI for de.NBI VO and join the project: LLMCloud24 via provided registration link
- try to login at the de.NBI Cloud Berlin dashboard: https://denbi-cloud.bihealth.org

## 2. How to deploy an vm:

>[!IMPORTANT]
>We generally recommend that you generate your own key pair (`ssh-keygen` command can be used), and then upload the public key to the de.NBI cloud portal AND the OpenStack Dashboard.
>With this method, you are also less likely to run into issues. If you don't know which one is the public or private key, just open them in a text editor. The private key will tell you it's a private key.

- Create your pair of keys in the horizon dashboard: https://cloud.denbi.de/wiki/quickstart/#ssh-setup
- Upload your public key in the de.NBI cloud portal: https://cloud.denbi.de/portal/webapp/#/userinfo
- How to create your own vm: https://cloud.denbi.de/wiki/Compute_Center/Berlin/#deploy-your-vms
  - you can choose to create VM with:
    - Details --> Instance Name: cloudvm-$yourName
    - Source --> create new Volume: yes and choose Image: Ubuntu-24.04-20240702
    - Flavor --> de.NBI default
    - Networks --> LLMcloud24-network-2
    - Key Pair --> add your own available Key Pair
- Assign a floating ip from "public 2" pool to your VM
- How to connect to your vm with ssh: https://cloud.denbi.de/wiki/Compute_Center/Berlin/#connect-to-your-vms-with-ssh
  - public key needs to be uploaded in cloud portal: https://cloud.denbi.de/portal/webapp/#/userinfo
  - pulic key needs to be added during the creation of the vm: https://cloud.denbi.de/wiki/quickstart/#floating-ip
  - you would need to setup a ProxyJump in order to connect to your own VM e.g. provide a configuration similar to this one:

>[!NOTE]
>Some general notes about your ssh config entries:
>
>**Host**: can be anything you like, you will use it often like this: `ssh my-host`
>
>**HostName**: this must either be a domain or an IP
>
>**User**: this will be your LifeScienceLogin ID found at https://cloud.denbi.de/portal/webapp/#/userinfo
>
>**IdentityFile**: this should be the full path to your **private** key, see important note above
>
>**ProxyJump denbi-jumphost-01.bihealth.org** keep this line for your de.NBI VMs

```
Host denbi-jumphost
    HostName denbi-jumphost-01.bihealth.org
    User {LifeScienceLogin}
    IdentityFile {PATH_TO_PRIVATE_KEY}
    ServerAliveInterval 120

Host {NAME_OF_VM}
    HostName {172.16.XXX.XXX}
    IdentityFile {PATH_TO_PRIVATE_KEY}
    User {ubuntu / centos}
    ProxyJump denbi-jumphost
```
## 3. How to add more storage to your vm: 
- https://cloud.denbi.de/wiki/Compute_Center/Berlin/#storage
## 4. How to use the openstack api: 
- https://cloud.denbi.de/wiki/Compute_Center/Berlin/#using-the-openstack-api
