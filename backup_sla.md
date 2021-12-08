Backup Service Level Agreement (SLA)
_______________

Backup coverage

Manual restoration via ansible playbook backup:
- App service (Agama) - covered by ansible repo
- Web service (Nginx) - covered by ansible repo
- DNS service (Bind9) - covered by ansible repo
- Database service (InfluxDB, MySQL) - backed up daily
- Monitoring services (Grafana, Exporters) - covered by ansible repo
- Ansible repo - backed up daily

______________________________
RPO (recovery point objective)

The backup will restore the database to an identical point in no more than one day in the past.
________________________
Versioning and retention

Local backup is made once a day at 3:30 in the morning. Includes: InfluxDB, MySQL and ansible repository.
Local backups are deleted once a day right before new backup is made. Includes: InfluxDB, MySQL and ansible repository.

Full backup is made every Sunday at 3:30 in the morning. Includes: InfluxDB, MySQL and ansible repository.
Full backups are kept for one month. Includes: InfluxDB, MySQL and ansible repository.

________________
Usability checks

Backup recovery can be verified by using administration tools on virtual environment comparing database dump to live database. 

____________________
Restoration criteria

Restoration occurs only at the time when there is an actual problem with the service that could not be reversed. 
These include: files deleted by an accident, damaged files, data loss, security breach (malware, ransomware).

_____________________________
RTO (recovery time objective)

Restoring of a backup will take no longer than 3 hours to guarantee minimal process downtimes.
