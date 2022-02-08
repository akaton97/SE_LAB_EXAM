# SE_exam_project

MY NOTES
First off, go to github and download the entire 
GITHUB

BUILD THE CLIENT AS LAST ONE.
BUILD ORDER: DB-> Every Server -> CLIENT
RUN ORDER: DB-> Every Serve -> CLIENT

NEVER RUN THE SINGLE *.java FILES, BUT ALWAYS THE ENTIRE PROJECT (because the pom.xml should be included)

MAVEN "HTTPS ERROR", check the following links:
>https://stackoverflow.com/questions/60031044/how-to-change-mavens-remote-repository-url-in-the-netbeans-ide-from-http-to-ht
>https://maven.apache.org/download.cgi
the problem here is that netbeans of the virtual machine is old and its maven version is 

MAVEN COMMANDS:
>mvm (clean) install: install pom file in a directory, never write files name. It install all pom in a directory

!!! "SET CONFIGURATION" FOR RUN DO NOT ACTUALLY RUN THE CODE AFTER, BUT YOU HAVE TO DO IT MANUALLY !!!
!!! THE PATH OF MAIN CLASS IN POM SHOULD MATCH THE "MAIN".java OF EVERY PROJECT !!!

ISTRUCTION FOR POM
>se non dovesse compilare, controlla che nel POM ci sia sta roba sotto:
<!-- sta parte serve per far compilare bene -->
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <configuration>
      <source>1.8</source>
      <target>1.8</target>
  </configuration>
</plugin>
<!--AO-->

FOREIGN KEY - DATASET
SE il testo d'esame presenta delle classi/oggetti che sono legati tramite foreign key, bisogna
implementare un adattore con marshal (vedi esame MOVIE-SOAP-DB)

alt+Ins (sopra canc) su una classe per aprire un menù contestuale per la creazione di getter e setter

OTHERS NOTES
if maven not installed on archlinux: sudo pacman -S maven

to run server or client with intellij:  
sul terminale: mvn compile  
then run

>if exception, to add dependences:  
inside pom file (on blank space): click R button -> generate -> dependences -> search for the required dependency

to see processes on ports (ex: 8080):  fuser 8080/tcp   
to remove processes on ports (ex: 8080):  fuser -k 8080/tcp  

to create jar: add dependency on pom and on terminal mvn package  
check if a folder named target is created with a .jar file inside

----------------------------------------------------------------------------------------

GRPC  
https://github.com/lrazovic/grpc-comparison  

----------------------------------------------------------------------------------------
DOCKER - JMS 

to activate activemq on labs or exams if needed (in JMS examples):  
sudo docker pull rmohr/activemq  
sudo docker run -p 61616:61616 -p 8161:8161 rmohr/activemq  
http://localhost:8161 (check connection)  

to install docker:  
https://www.simplilearn.com/tutorials/docker-tutorial/how-to-install-docker-on-ubuntu  

to solve docker-compose problem:  
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)"  -o /usr/local/bin/docker-compose  
sudo mv /usr/local/bin/docker-compose /usr/bin/docker-compose  
sudo chmod +x /usr/bin/docker-compose  

docker commands:  
docker ps    (list of all active containers)  
docker stop "container_name"   (stops that container)

----------------------------------------------------------------------------------------

to see versions of java installed:  
archlinux -> sudo archlinux-java status  
linux -> java -version

to install java16:  
sudo pacman -Syu jdk-openjdk

to solve glibc problem:  
pacman -Sw glibc lib32-glibc  
pacman -S glibc lib32-glibc

to set the wanted version of java:  
sudo archlinux-java set "nome versione stampata in precedenza"

(alternative way to install java16 on archlinux):  
to check if it is installed: java -version  
install jre in arch linux: sudo pacman -sS java | grep jre  
install latest version of jre: sudo pacman -S jre-openjdk  
to install jdk in archlinux: sudo pacman -sS java | grep jdk  
install latest version of jdk: sudo pacman -S jdk-openjdk  

--------------------------------------------------------------------------- 
CREARE PROGETTO MAVEN IN NETBEANS  
new project -> maven -> java application -> i pacchetti chiamali tipo it.uniroma1  
 
--------------------------------------------------------------------------- 
HOW TO CREATE DATABASE  
notes: create in a "easy to reach" directory;
>da terminale: sqlite3 "nomeDB".db  
.databases  

>metto path dentro ai paramentri (run->set configuration) della configurazione del DB con secondo parametro "create"  
es: "path" create  

>poi per verificare il contenuto del db: path "stringa scelta"    (dentro a configurazione)  
  
oppure:  
da terminale: sqlite3 path/"nomeDB".db

NB: quando devo inserire il path, se metto le virgolette " " al path mi prende anche gli spazi nei nomi delle cartelle   

---------------------------------------------------------------------------

 CREATE .jar FILE  
 mvn package (nel ternimale) e crea un .jar file nella cartella target
 
--------------------------------------------------------------------------
 SOAP  
 dentro a WSInterface.java bisogna aggiungere @WebService e l'import  
 dentro a WSImplService-java bisogna aggiungere @WebService(endpointInterface ecc..)  
 
 per vedere gli elementi del db con soap andare su: "http://0.0.0.0:7070/WSInterface?wsdl"  
 !!fai attenzione alla connessione tra il SOAP e il db (WSImpl -> setConnection)!!
 ------------------------------------------------------------------------------  
 REST  

 per vedere gli elementi del db con rest andare su: "http://localhost:8080/"  

