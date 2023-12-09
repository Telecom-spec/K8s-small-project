Here two applications has been deployed.
1. Springboot
2. MongoDB.

The Springboot application has been deployed with NodePort so that users from outside can able to access the application.
Deployment details for spring application is in spring-svc.yml file.

The MongoDB application has been deployed with ClusterIP so that Springboot application can able to communicate with MongoDB via the clusterIP.
Here the MongoDB is storing data into storage PV through PVC.
But storage PV is configured as Static Volume, which means you need to create PV volume before deploying the MongoDB application with PVC.
Here the storage is configured as NFS storage and PV is configured using the NFS server details.
Deployment details for MongoDB application with PVC is in mongo-svc-pvc.yml.
PV details is specified in pv_withoutstcla.yml, pv1_withoutstcla.yml and pv2_withhostpath.yml.

Details of PV yml files as below
pv_withoutstcla.yml = No StorageClass, Capacity 10Gi and persistentVolumeReclaimPolicy: Retain (Volume as NFS)
pv1_withoutstcla.yml = No StorageClass, Capacity 10Gi and persistentVolumeReclaimPolicy: Delete (Volume as NFS)
pv2_withhostpath = No StorageClass, Capacity 5Gi and persistentVolumeReclaimPolicy: Delete (Volume as Hostpath)

Diagram is in file named Spring-MongoDB-with staticVol


