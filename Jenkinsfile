pipeline{   
    agent any
    stages {
        stage("Build Maven") {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mohdfaaiz/GitWebHook']]])
            }
        }       
       stage('Build'){
            steps{
                sh 'mvn clean install'
            }
         }
          stage('SonarQube analysis') {
        steps{
        withSonarQubeEnv('sonarqube-9.2.2') { 
        sh "mvn sonar:sonar"
    }
        }

   
       
    }
}

//test jekins webhook
//twaa
