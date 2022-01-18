This document describes SLA (Service Level Agreement)


*******************
1. Backup coverage:
*1.1 Following services can be manually restored using ansible playbook:
- Web service (Nginx)
- App service (AGAMA)
- Monitoring service (Prometheus, Prometheus exporters, Grafana)
- DNS service (Bind)

*1.2 Following services are backed up on daily bases:
- Database service (MySQL)
- Metrics/Logs Database service (InfluxDB)
- Ansible repository


*********************************
2. RPO (Recovery Point Objective)
*2.1 The backup will allow to restore Databases (paragraph 1.2) to state no more than one day in the past.


***************************
3. Versioning and retention
Following parts are applied to services mentioned in part 1.2
*3.1 
    3.1.1 Local backup is created every day at 22:00 UTC and 10:00 UTC. 
    3.1.2 Local backup is stored for one day until it is replaced with a new one.

*3.2
    3.2.1 Full backups are created every Sunday at 22:10 UTC.
    3.2.2 Full backups are stored for at least 30 days.
    3.2.3 Incremental backups are created every day of the week except of Sunday at 22:10 UTC.


*******************
4. Usability checks
*4.1 Usability can be checked using administration tool by comparison of database dump and live database.


***********************
5. Restoration criteria
*5.1 Restoration happens only, when problems with service can't be reversed. This includes: damaged files, data loss, security breach.


********************************
6. RTO (Recovery Time Objective)
*6.1 Services functioning will be recovered in no less than 2 hours.