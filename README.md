# wp-project
Deploy Wordpress in K8s
I deploy small lab in Minikube
2 things are important: 
-- Local Volume and  Name of NODE
-- Create Database name: Wordpress in your POD

kubectl appy -f mysql-secret.yaml
kubectl appy -f mysql-volume.yaml
kubectl appy -f mysql-deployment.yaml
kubectl appy -f mysql-service.yaml

When you deploy PV and PVC -> Focus on local storage
local:
    path: "/mnt/wpdata" --> YOu should create it before deploy PV
  nodeAffinity:
    required:
      nodeSelectorTerms:
      - matchExpressions:
        - key: kubernetes.io/hostname
          operator: In
          values:
          - centos8 #name of the Node
                    
          
 local:
    path: "/mnt/mysqldata" --> YOu should create it before deploy PV
  nodeAffinity:
    required:
      nodeSelectorTerms:
      - matchExpressions:
        - key: kubernetes.io/hostname
          operator: In
          values:
          - centos8 #name of the Node
