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
      
      def mvnHome = tool name: 'maven3', type: 'maven'
      withSonarQubeEnv('sonarone'){
       sh "${mvnHome}/bin/mvn sonar:sonar"
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





