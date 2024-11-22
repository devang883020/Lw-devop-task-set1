# Lw-devop-task-set1
task-2:
 Scenario: Configuring Persistent Storage in
 Kubernetes for a Stateful Application
 You need to deploy a MySQL database on Kubernetes with persistent
 storage so that the data is not lost even if the pod restarts.

 How would you configure persistent storage for the MySQL database?
 Instructions:
 Create a Persistent Volume (PV) of storage 1Gi &
 accessModes of ReadWriteOnce
 Create a Deployment for the MySQL Database with PVC
 with image mysql:5.7


I've created a complete Kubernetes configuration that includes:

A Persistent Volume (PV) that:
Provides 1Gi of storage
Uses ReadWriteOnce access mode
Uses hostPath for demonstration (you should use an appropriate storage class in production)

A Persistent Volume Claim (PVC) that:
Claims the storage from the PV
Matches the access mode and storage size

A Secret for storing the MySQL root password securely
A MySQL Deployment that:
Uses mysql:5.7 image
Mounts the persistent storage
Uses the secret for the root password
Configures the necessary ports



To apply these configurations:
bashCopykubectl apply -f mysql-config.yaml
Important notes:

The hostPath storage type is used for demonstration. In production, use an appropriate storage class for your environment (like AWS EBS, Azure Disk, etc.).
The password is base64 encoded but should be changed in production.
Consider adding a Service if you need to access the database from other pods.
