pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later yes
            }
        }   
      stage ('Docker build and push') {
          steps {
              sh 'printenv'
              sh 'docker build -t saikrishna310/numeric-app:""$Git_Commit"" .'
              sh 'docker push saikrishna310/numeric-app:""$Git_Commit""'
          }  
      } 
    }
}
