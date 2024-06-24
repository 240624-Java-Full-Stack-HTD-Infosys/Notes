# GCP Cloud Storage
There are a number of storage options available within the GCP ecosystem. 
 - Persistent Disk - Logical volumes striped across hundreds of physical HDDs
 - Hyperdisk - Fast redundant storage volumes that dynamically resize
 - Local SSDs - Physical SSDs attached to the machine hosting your VMs
 - Cloud Storage Buckets - Object storage
 - Firestore - Scalable NoSQL database
 - Cloud SQL - Scalable SQL database

## Persistent Disk
The first few entries above are made to be redundant. Persistent disks are "striped" across multiple physical disks. Striping is a feature to increase HDD speeds and is most likely also offering some amount of redundancy, like RAID 5. (In fact it probably is RAID 5).  

These disks can be in a particular zone, which is one or more data centers in a particular geographic region. We can also use regional persistent disk volumes which replicate data between zones and offers fault tolerance in case one zone goes down.

## GCP Hyperdisk
This is the fastest of the redundant storage options. According to GCP documentation: "Hyperdisk offers substantially higher performance, flexibility and efficiency." Hyperdisk does this by decoupling and scaling storage processing. There are three Hyperdisk flavors:
 - Balanced - good for a wide variety of use cases
 - Extreme - highest performance for the most demanding workloads
 - Throughput - flexible capacity for horizontally-scaled workloads like Hadoop and Kafka

## Local SSDs
These drives are physically attached to the hardware on which your VMs run, giving them very high throughput and very low latency. These drives are not persistent! If the VM is stopped or deleted the data is gone. Local SSDs are also fixed in size, being exactly 375GB.

## Cloud Storage Buckets
These are the most flexible of all the solutions mentioned here. Like the others this offers "block storage" (the way computers store most data), but also offers "object storage". These things aren't mutually exclusive, buckets do both. Block storage refers to the way data is written to disks. Object storage refers to the way we interact with the data. GCP Storage Buckets are RESTful, and the objects (files) are the resources. The objects can be made accessible to other GCP services which can GET, POST, and DELETE the files. They can even be opened up to the public internet.

If you don't need low latency and high speed offered by the faster options above, buckets are a good choice for most uses. Cloud Storage Buckets do have different performance options based on the storage class of each object:
 - Standard - typical availability and cost, no minimum storage duration, no retrival fees
 - Nearline - lower cost for storage at rest, lower availability, minimum duration 30 days, costs for retriving data
 - Coldline - even lower costs for storage at rest, 90 day duration, higher retrival fees
 - Archive - lowest cost for storage at rest, 1 year minimum duration, highest retrival fees

These solutions don't typically impact the speed of retriving data, the data should always be available within miliseconds. Everything other than standard costs fees to retrieve data, each one offering lower cost to store the data, but greater cost to retrieve it.

### Firestore & Cloud SQL
Storing data in databases is extremely common. Database files could be stored in any block storage, so the above options are all available to us. But, even better than storing the files ourselves, just run the entire database in the cloud, where it will make best use of the storage options available.

Google offers Google Cloud SQL, which will run a sql database engine on a GCP server and will store the files on HDDs or SSDs.

Firestore is a NoSQL option which uses its own non-relational data model. 
