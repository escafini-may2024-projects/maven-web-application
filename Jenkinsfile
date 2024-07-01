node{
    
echo "Job name is: ${env.JOB_NAME}"
echo "Build number is: ${env.BUILD_NUMBER}"
echo "Jenkins Home is: ${env.JENKINS_HOME}"
echo "Build Number is: ${env.BUILD_NUMBER}"
    
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
	
	def mavenHome = tool name: 'maven3.9.8'
	
stage('CheckOutCode'){
git branch: 'development', credentialsId: 'bf29b7e6-5cf4-404a-b39b-cf74f0f3c1c0', url: 'https://github.com/escafini-may2024-projects/maven-web-application.git'
}
	
stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*	
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
	
stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}
	
stage('DeployAppIntoTomcat'){
sshagent(['47a15132-52ee-4e3e-a921-cba2e5f76760']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.14.7:/opt/apache-tomcat-9.0.89/webapps/"
}
}
*/	
	
}
