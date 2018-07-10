
node('master') 
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/dibya-jenkins/maven1.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war ubuntu@13.127.27.227:/var/lib/tomcat7/webapps/QAenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
      sh 'java -jar /home/ubuntu/.jenkins/workspace/Scripted_Pipeline/testing.jar'  
    }
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for approval', submitter: 'Sheshi'
        sh 'scp /home/ubuntu/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war ubuntu@10.10.10.53:/var/lib/tomcat7/webapps/PRODenv.war'
    }
    
    
    
    
    
}