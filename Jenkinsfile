 pipeline {
    agent {label 'mavenlabel'}

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }
     
     stage ('sonarqube analysis'){
      steps{
      withSonarQubeEnv('sonarone'){
       sh 'mvn package sonar:sonar'
      }
      }
     }
      


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn install'
                }
            }
        }
    }
}





