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
