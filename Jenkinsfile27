node{
  def mavenHome = tool name: 'maven3.8.4'
  stage('1.Clone'){
    git branch: 'master', credentialsId: 'Git_Credentials', url: 'https://github.com/LandmakTechnology/paypal-web-app'
  }
  stage('2.MavenBuild'){
    sh "${mavenHome}/bin/mvn clean package"
   // bat 'mvn package'
  }
   /*   stage('3.CodeQuality'){
    sh "${mavenHome}/bin/mvn sonar:sonar"
  }
    stage('4.UploadArtifacts'){
    sh "${mavenHome}/bin/mvn deploy"
  }
      stage('6.Deploy2dev'){
      deploy adapters: [tomcat9(credentialsId: 'Tomcat_Credentials', path: '', url: 'http://18.207.210.70:8080/')], contextPath: null, war: 'target/web-app.war'
}
      stage('5.Deploy2uat'){
        sshagent(['agentcredentials']) {
       // sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.89.218:/opt/tomcat9/webapps/uat.war"
        
}
      
      }
          stage('7.approval'){
      timeout(time:8, unit:'HOURS'){
      input message: 'Please approve deployment to Production'
      }
     }
   stage('8.Deploy2prod'){
        sshagent(['agentcredentials']) {
        sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.89.218:/opt/tomcat9/webapps/app.war"
        
}
      
      }
      stage('9.EmailAlerts'){
    emailext body: '''Hi

Build status for boa app.

Regards,
Landmark Technologies''', recipientProviders: [developers(), requestor()], subject: 'Project status', to: 'boa@gmail.com'
   }
   */
}
