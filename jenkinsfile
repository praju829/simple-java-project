pipeline {
  agent any 
  stages {
   stage('Test') {
      steps {
        echo 'Testing...'
        snykSecurity(
          snykInstallation: 'snyk',
          snykTokenId: 'snyk cred'
        )
      }
    }
    stage ('SAST') {
      steps {
        withSonarQubeEnv('SonarQube') {
          sh 'mvn package'
          sh 'mvn sonar:sonar'
          sh 'cat target/sonar/report-task.txt'
        }
      }
    }
  }
}
