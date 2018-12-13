pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean compile'
                }
            }
        }
        
    stage ('SonarQube Analysis') {
        
        def mvnHome =  tool name: 'maven_3_5_0', type: 'maven'
         withSonarQubeEnv('sonar-6') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"

          }
       }
      

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
   

   

   

