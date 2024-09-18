# Checklist how to operate a service

0. **Housekeeping**
   - [ ] Who will be responsible to keep the service running?
   - [ ] Who will be the backup of this person?
   - [ ] Ensure you document your service architecture
   - [ ] Clean up old and delete unnecessary files to free up space.
   - [ ] Version control your service's configuration files using Git to track changes and easily revert if necessary.
   - [ ] Clean up old and delete unnecessary files to free up space.

1. **Monitoring and Alerting**
   - [ ] Monitor uptime and response time of the web service using a tool like UptimeRobot
   - [ ] Set up alerts to notify you when the site goes down or if response times exceed a threshold.

2. **Backup and Restore**
   - [ ] Automate backups of the application files and databases daily (use cron jobs or backup services like rsync)
   - [ ] Regularly back up key configuration files
   - [ ] Version control your service's configuration files using Git to track changes and easily revert if necessary.
   - [ ] Test backups at least once a month to ensure they are restorable.

3. **Security Management**
   - [ ] Apply automatic security updates for your operating system and web server software (e.g., Nginx).
   - [ ] Update application dependencies (web frameworks, libraries) to patch vulnerabilities and maintain compatibility.
   - [ ] Set up SSL/TLS certificates using Let's Encrypt or your hosting provider, and ensure auto-renewal is working.

4. **Incident Management**
   - [ ] Have a simple incident response plan: Identify what to do when the service goes down (e.g., restart server, clear cache, check logs).
   - [ ] Keep a checklist or script handy for common fixes (restart services, rollback deployments, troubleshoot network issues).
   - [ ] Track any downtime or performance degradation, noting how it was resolved.

5. **Automation**
   - [ ] Automate deployments using a basic shell or more advanced with Ansible.
   - [ ] Automate routine server tasks (e.g., restarting services, rotating logs, cleaning temp files) with simple cron jobs.

### Tools and Services to Help:
- [ ] **Monitoring & Alerting**: UptimeRobot
- [ ] **Backup Automation**: rsync, cron jobs
- [ ] **Security**: Let's Encrypt (for SSL)
- [ ] **Incident Handling**: bash/ptyhon scripts or ansible playbooks for server management, uptime monitoring services, documentation
