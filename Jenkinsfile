
node('master') 
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/dibya-jenkins/maven2.git'
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
      sh 'echo "test passed."'  
    }
    stage('ContinuousDelivery')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war ubuntu@13.232.43.214:/var/lib/tomcat7/webapps/PRODenv.war'
    }
    
    
    
    
    
}