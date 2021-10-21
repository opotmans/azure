https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/

1. create a folder on the node ex: /opt/data
<br> --> Question : which rights do we need to gives to this directory
2. create a persistent volume (you could also create ephemeral volume)
<br> ex:

[!NOTE]
bonjour 

~~~~ 
apiVersion: v1
kind: PersistentVolume
metadata:
  name: task-pv-volume
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
~~~~
