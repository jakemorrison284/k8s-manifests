# Redis Configuration and Backup Procedures

## Overview
This document outlines the configuration and backup procedures for Redis used within the payments-core application in the Novapay namespace.

## Redis Configuration
- **Redis URL**: The Redis instance is accessed via the secret `novapay-secrets` with the key `redis-url`.
- **Backup Location**: Backups are stored in the `/backup` directory of the container.

## Backup Strategy
- **Volume**: An empty directory volume is created for backups. This volume can be mounted to any container needing access to backup files.
- **Backup Frequency**: Define a backup frequency based on application needs. For example, backups can be scheduled using a CronJob to run every hour.
- **Backup Process**: The backup process should include:
  - Dumping the Redis data using `redis-cli save`.
  - Copying the dump file to the mounted `/backup` directory.

## Restoring from Backup
To restore Redis from a backup, copy the dump file from the `/backup` directory back to the Redis data directory using:
```bash
cp /backup/dump.rdb /data/dump.rdb
```

## Monitoring and Alerts
Implement monitoring for the backup process to ensure it runs successfully and send alerts in case of failures.

## Conclusion
This document serves as a guideline for the Redis configuration and backup procedures. Ensure to adhere to these practices to maintain data integrity and availability.