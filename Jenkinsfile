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
            withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
                sh 'printenv'
                sh 'docker build -t saikrishna310/numeric-app:""$GIT_COMMIT"" .'
                sh 'docker push saikrishna310/numeric-app:""$GIT_COMMIT""'
            }
          }  
      } 
    }
}
