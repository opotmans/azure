`<addr>
opotmans@Lubuntu:~/Repos/azure$ git config --global user.email "potmans@hotmail.com"
opotmans@Lubuntu:~/Repos/azure$ git config --global user.name "opotmans"
opotmans@Lubuntu:~/Repos/azure$ git init
Dépôt Git existant réinitialisé dans /home/opotmans/Repos/azure/.git/
opotmans@Lubuntu:~/Repos/azure$ git remote add origin https://github.com/opotmans/azure.git
opotmans@Lubuntu:~/Repos/azure$ git branch -M master
opotmans@Lubuntu:~/Repos/azure$ git commit -m "first commit"
[master (commit racine) de6aa88] first commit
 1 file changed, 15 insertions(+)
 create mode 100644 Kubernetes_manifests/pod.yaml
opotmans@Lubuntu:~/Repos/azure$ git push -u origin master
Énumération des objets: 4, fait.
Décompte des objets: 100% (4/4), fait.
Compression par delta en utilisant jusqu'à 8 fils d'exécution
Compression des objets: 100% (2/2), fait.
Écriture des objets: 100% (4/4), 402 octets | 201.00 Kio/s, fait.
Total 4 (delta 0), réutilisés 0 (delta 0), réutilisés du pack 0
To https://github.com/opotmans/azure.git
 * [new branch]      master -> master
La branche 'master' est paramétrée pour suivre la branche distante 'master' depuis 'origin'.
Copy repository


Problem of no access to coredns resolution
--> need to activate the module br_netfilter and put it otherwise, the kubeproxy doesn't work and the system doesn't use the iptables. So the IP for the services are not accessible

problem of the installation of flannel

log of the flannel container :

* I used kubeadm to initialize my K8 master. However, I missed the --pod-network-cidr=10.244.0.0/16 flag 


to replace the CIRD in the kube-flannel.yaml in the config 
$ kubectl edit cm kube-flannel-cfg -n kube-system
net-conf.json: | { "Network": "10.244.0.0/16", "Backend": { "Type": "vxlan" } }

kubectl patch node kubernetes-master -p '{ "spec": { "podCIDR": "10.244.0.0/16"} }'

{
    "apiVersion": "v1",
    "kind": "Node",
    "metadata": {
        "annotations": {
            "kubeadm.alpha.kubernetes.io/cri-socket": "/var/run/crio/crio.sock",
            "node.alpha.kubernetes.io/ttl": "0",
            "volumes.kubernetes.io/controller-managed-attach-detach": "true"
        },
        "creationTimestamp": "2021-07-29T08:51:24Z",
        "labels": {
            "beta.kubernetes.io/arch": "amd64",
            "beta.kubernetes.io/os": "linux",
            "kubernetes.io/arch": "amd64",
            "kubernetes.io/hostname": "kubernetes-master",
            "kubernetes.io/os": "linux",
            "node-role.kubernetes.io/control-plane": "",
            "node-role.kubernetes.io/master": "",
            "node.kubernetes.io/exclude-from-external-load-balancers": ""
        },
        "name": "kubernetes-master",
        "resourceVersion": "444147",
        "uid": "0b9c8288-e5eb-436d-90e5-de11c1f205d2"
    },
    "spec": {
       "podCIDR": "10.244.0.0/16",
       "podCIDRs": [
            "10.244.0.0/16"
       ]
    },
....