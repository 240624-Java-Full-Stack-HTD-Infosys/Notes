# GCP Cloud SQL
Cloud SQL is a fully managed relational database service from Google Cloud Platform. This is one of the most common and ubiquitous services they offer, and they boast that 95 of their top 100 customers all use Cloud SQL. Managing a database requires more than just a server with some software. You need backups, fault tolerance, replication, security, and frequent updates. You also have to manage the storage capacity as your databases grow. Google's SQL service can handle all of this, and integrates with the rest of the platform.

## Engines
Google Cloud SQL supports many open-source as well as commercial SQL engines, including MySQL, PostgreSQL, and MS SQL Server. 

## Scalable
Both processing speed and storage capacity can be scaled dynamically as your needs change, leading to cost-effectiveness as you only pay for the resources you need. Small and little-used databases can start out cheap, and grow as your needs do.

## GCP Integration
As with everything in GCP, this service is designed to fully integrate with the rest of the platform. You can, for instance, authorize your Compute Engine VMs to access the database without opening it up to the public internet.

## Storage
GCP Cloud SQL stores your database file(s) on either hard disks or solid-state disks. The default would be SSDs which offer fast and predictable storage. If you have very large databases and can tolerate higher latency, HDDs might be a better solution.