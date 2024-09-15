# How to cloud

Our first day will give you an introduction to the setup of our OpenStack Cloud, so you are prepared to start a virtual machine and work on your own project.

1. Introduction to cloud portal: **https://cloud.denbi.de/portal**
  - further explanation of the cloud portal: https://cloud.denbi.de/wiki/portal/allocation/
2. Introduction to OpenStack cloud via de.NBI Cloud wiki: **https://cloud.denbi.de/wiki/quickstart**
  - A brief overview of the OpenStack concepts can be found here: https://cloud.denbi.de/wiki/Concept/basics/
  - A brief overview of the general OpenStack components can be found here: https://cloud.denbi.de/wiki/Concept/openstack/
3. Specific Information about de.NBI Cloud site in Berlin: **https://cloud.denbi.de/wiki/Compute_Center/Berlin**

## Hands-on part

## Join the LLMcloud24 project in de.NBI Cloud Berlin
- register via LifeScience AAI for de.NBI VO and join the project: LLMCloud24 via provided registration link
- try to login at the de.NBI Cloud Berlin dashboard: https://denbi-cloud.bihealth.org

### Deploy your first VM  
- create your pair of keys in the horizon dashboard: https://cloud.denbi.de/wiki/quickstart/#ssh-setup
- upload your public key in the de.NBI cloud portal: https://cloud.denbi.de/portal/webapp/#/userinfo
- how to create your own vm: https://cloud.denbi.de/wiki/Compute_Center/Berlin/#deploy-your-vms
  - you can choose to create VM with:
    - Details --> Instance Name: cloudvm-$yourName
    - Source --> create new Volume: yes and choose Image: Ubuntu-24.04-20240702
    - Flavor --> de.NBI default
    - Networks --> LLMcloud24-network-2
    - Key Pair --> add your own available Key Pair
      and launch the Instance.
- how to connect to your vm with ssh: https://cloud.denbi.de/wiki/Compute_Center/Berlin/#connect-to-your-vms-with-ssh
- how to add more storage to your vm: https://cloud.denbi.de/wiki/Compute_Center/Berlin/#storage
- how to use the openstack api: https://cloud.denbi.de/wiki/Compute_Center/Berlin/#using-the-openstack-api
