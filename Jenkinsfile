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
         stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Sonarqube"
    }
  }
   
       
    }
}

//test jekins webhook
//twaa
