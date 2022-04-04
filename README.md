Cluster için
----

clusterı oluşturmak için içerikte yer alan cfn-create-k8s-cluster template kullanarak 1master-2workerdan oluşan cluster ı kurabilirsiniz.

-----

Master-node bağlandıktan sonra
-namespacelerimizi oluşturalım
 - kubectl create namespace devops-tools
 - kubectl create namespace nexus

-----
Jenkins ile nexus kurulumu için jenkins-manifest ve nexus-manifest dosyaları çalıştırabilirsiniz 

Service yamllara göre ilgili portları düzenlemeyi unutmayalım(security-groups)

jenkins e girmek için giriş passwordunu aşağıdaki komut ile alabilirsiniz.
 - kubectl exec  "your_pod" cat  /var/jenkins_home/secrets/initialAdminPassword -n devops-tools

nexus a girmek için giriş passwordunu aşağıdaki komut ile alabilirsiniz.
 - kubectl exec "your_pod" -n nexus cat /nexus-data/admin.password

-----
Jenkins kısmında github için "ssh-keygen -f simple-java-app-jenkins-github-deploy-key -m PEM" ile keylerimizi oluşturup public olanı github private olanı 
jenkins ekledik.(jenkins Credentials kısmında)
Repomuzu tanıttıktan sonra github webhook için ayarlamalar yapıldı.(Payload URL kısmında public.ip:32000 )

Sonrasında jenkins Global Tool Configuration ayarlamalar yapıldı. (öncesinde ilgili plug-in'ler yüklendi)
