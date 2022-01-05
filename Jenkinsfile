node { 
    def MHD = tool name: 'maven3.84'

stage ('1.Initiation') {
sh "echo tart deployment"

}
stage('2.Clone') {
git branch: 'dev', credentialsId: 'Github-Credentials', url: 'https://github.com/Ndolino/web-app'
}

stage('3.Mavenbuild') {
    
sh "${MHD}/bin/mvn clean package " 
}
stage('4.CodeQuality') {
sh "${MHD}/bin/mvn sonar:sonar " 
}
stage('5.uploadsArtifacts') {
sh "${MHD}/bin/mvn deploy" 
}
stage('5.udeploy') {
deploy adapters: [tomcat9(credentialsId: 'Tomcat-Credentials', path: '', url: 'http://35.189.73.133:8080/')], contextPath: null, war: '**/*.war'

}
stage('emailNotification'){
   emailext body: '''Hello All,
See statust of build from Dev BMO pipe;ine project.
Regards.
Devops Eng Team''', subject: 'Build Status', to: 'micheltaxclinicvolun20@gmail.com michelgm276@gmail.com'
}
}
