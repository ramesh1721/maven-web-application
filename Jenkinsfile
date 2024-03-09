/*node{

//properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

echo "The Job name is: ${env.JOB_NAME}"
echo "The Nod ename is: ${env.NODE_NAME}"
echo "The Build Number is: ${env.BUILD_NUMBER}"
echo "The Jenkins Home directory is: ${JENKINS_HOME}"

def mavenHome = tool name: "maven3.6.3"

try{
sendSlackNotifications("STARTED")

stage('CheckoutCode'){
git branch: 'master', credentialsId: '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', url: 'https://github.com/ramesh1721/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn deploy"
}

stage('DeployAppIntoTomcatServer'){
sshagent(['48c992f5-c73e-40ba-b71b-9191b6f93285']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.10.36:/usr/local/apache-tomcat-9.0.70/webapps/" 
}
}


}//try closing
catch(e){
currentBuild.result = "FAILURE"
}
finally{
sendSlackNotifications(currentBuild.result)
}
  
}*/
pipeline {
  agent any
  tools {
    maven '3.6.3'
  }
  stages{
    stage('git checkout') {
      steps {
        git branch: 'master', credentialsId: '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', url: 'https://github.com/ramesh1721/maven-web-application.git'
      }
    }
    stage ('build') {
      steps {
        sh'mvn --version'
      }
    }
  }
}