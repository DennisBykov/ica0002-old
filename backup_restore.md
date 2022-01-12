---------------Backup restore procedure---------------


1. MySQL database restoration
To rsetore MySQL database you need to run following commands on MySQL master host as root

1.1 To restore from backup server:

```sudo -u backup duplicity --no-encryption rsync://DennisBykov@backup.xoxoli.us//home/DennisBykov/mysql /home/backup/restore

```ls /home/backup/restore

```mysql agama < /home/backup/restore/agama.sql


1.2 To restore from local backup:

```mysql agama < /home/backup/mysql/agama.sql




2. InfluxDB database restoration
To restore InfluxDB database for telegraf run following commands on managed host as root

2.1 To restore from backup server:

```sudo -u backup duplicity --no-encryption rsync://DennisBykov@backup.xoxoli.us//home/DennisBykov/influxdb /home/backup/restore

```service telegraf stop

```influx -execute 'DROP DATABASE telegraf'

```influxd restore -portable -database telegraf /home/backup/restore

```service telegraf start


2.2 to restore from local backup

```service telegraf stop

```influx -execute 'DROP DATABASE telegraf'

```influxd restore -portable -database telegraf /home/backup/influxdb

```service telegraf start