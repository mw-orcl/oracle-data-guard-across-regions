# Introduction

Oracle Data Guard provide disaster recovery for your Oracle databases.  A standby database is set up to receive redo "transaction" logs from the primary database.  In the event of a disaster on the primary database, a failover to the standby database will occur.  

For disaster recovery, it is a best practice to set up the primary and standby database in two different data centers located in different geographies.  In this guide we will be setting up Oracle Data Guard between two cloud regions.  

Prerequisites

- Oracle Cloud Account with access to more than one region

- Oracle Cloud user role to manage networks and databases

- SSH public and private keys

- Compartment to work on

Although the primary database will be in one region and the standby in another region, they must both be in the same compartment.  And they must both not have overlapping VCN IP address blocks.

Estimated lab time:  30 minutes