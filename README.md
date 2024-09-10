# de.KCD Summer School 2024: Deploying LLMs in the Cloud

https://llmcloud2024.github.io

## Things that will be covered on Day 3
1. **Users get to set up and deploy their own LLM** (Sebastian)
2. **Users get to deploy and run their own BioCypher and BioChatter demos interfaced with their previously deployed LLM** (Sebastian)

## Things that can be covered on Day 4
1. **Monitoring and Alerting**
   - [ ] Monitor uptime and response time of the web service using a tool like UptimeRobot
   - [ ] Set up alerts to notify you when the site goes down or if response times exceed a threshold.

2. **Backup and Restore**
   - [ ] Automate backups of the web application files and databases daily (use cron jobs or backup services like rsync)
   - [ ] Regularly back up key configuration files (e.g., service server configurations, SSL certificates).
   - [ ] Test backups at least once a month to ensure they are restorable.

3. **Security Management**
   - [ ] Apply automatic security updates for your operating system and web server software (e.g., Nginx).
   - [ ] Set up SSL/TLS certificates using Let's Encrypt or your hosting provider, and ensure auto-renewal is working.

4. **Incident Management**
   - [ ] Have a simple incident response plan: Identify what to do when the service goes down (e.g., restart server, clear cache, check logs).
   - [ ] Keep a checklist or script handy for common fixes (restart services, rollback deployments, troubleshoot network issues).
   - [ ] Track any downtime or performance degradation, noting how it was resolved.

5. **Automation**
   - [ ] Automate deployments using a basic shell or more advanced with Ansible.
   - [ ] Automate routine server tasks (e.g., restarting services, rotating logs, cleaning temp files) with simple cron jobs.

6. **Configuration Management**
   - [ ] Version control your service's configuration files using Git to track changes and easily revert if necessary.
   - [ ] Ensure you document all server configurations and database connections for easy reference.
   - [ ] Use a password manager to securely store access credentials for servers, databases, and services.

7. **Regular Maintenance**
   - [ ] Update application dependencies (web frameworks, libraries) to patch vulnerabilities and maintain compatibility.
   - [ ] Clean up old and delete unnecessary files to free up space.

### Tools and Services to Help:
- [ ] **Monitoring & Alerting**: UptimeRobot
- [ ] **Backup Automation**: rsync, cron jobs
- [ ] **Security**: Let's Encrypt (for SSL)
- [ ] **Incident Handling**: bash scripts for server management, uptime monitoring services, documentation
