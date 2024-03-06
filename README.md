# maven

**It is possible to pass password in the mavne deploy in the command line?
**
It is working fine for me, we can define username and password variable mane anything, we choose, but we must use the repositoryId variable for the id in the settings.xml.


**It has been tested with maven version "Apache Maven 3.6.3 (Red Hat 3.6.3-13)"
**

Add this snippet to settings.xml :

<servers>
  <server>
    <id>${repositoryId}</id>
    <username>${repo.login}</username>
    <password>${repo.pwd}</password>
  </server>
</servers>

**Run this snippet to upload a file to Nexus :
**

mvn deploy:deploy-file -DrepositoryId=<repoid> -Drepo.login=<username> -Drepo.pwd=<password> -Durl=http://<url of Nuxus>:<port>/repository/<repository space> -Dfile=<file location> -DgroupId=<Group Id> -DartifactId=<artfact id>  -Dversion=<version> -Dpackaging=<packaging> -Dclassifier=<classifier> -X
