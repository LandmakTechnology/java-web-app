node{
    def MHD = tool name: "maven3.8.5"
    stage('code'){
        git branch: 'development', url: 'https://github.com/LandmakTechnology/web-app'
    }
    stage('BUILD'){
       sh "${MHD}/bin/mvn clean package"
 
    }
    /*
    stage('deploy'){
  sshagent(['tomcat']) {
  sh "scp -o StrictHostKeyChecking=no target/*war ec2-user@172.31.15.31:/opt/tomcat9/webapps/"
}
}
stage('email'){
emailext body: '''Build is over

Landmark
437212483''', recipientProviders: [developers(), requestor()], subject: 'Build', to: 'tdapp@gmail.com'
}
    */
}
