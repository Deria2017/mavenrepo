pipeline{
agent{label 'slave_1'}
stages{
stage(scm){
steps{
checkout([$class: 'GitSCM', branches: [[name: '*/feat01']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '54bdcde9-3db0-4536-aa75-b9e1edc34932', url: 'https://github.com/Deria2017/mavenrepo.git']]])
     }
 
          }
stage(mvn){
steps{
sh 'mvn package' 

}


          }
stage(sonar){
steps{
withSonarQubeEnv('sonar'){ 
sh 'mvn sonar:sonar'
}
     }
            }
     
stage(tomcat){
steps{
sh 'scp /root/workspace/first-pipeline/target/studentapp-2.1.1-FEAT01-SNAPSHOT.war root@54.236.52.78:/var/lib/tomcat/webapps'
     }

             }  


         }

       }
