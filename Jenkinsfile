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

node{
   stage('SCM Checkout'){
     git 'https://github.com/pnewalkar/CI-jenkins'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven_3_5_0', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   
   stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'maven_3_5_0', type: 'maven'
        withSonarQubeEnv('sonar-6') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"
        }
    }
   
//   stage('Email Notification'){
//      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
//      Thanks
//      Hari''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'pnewalkar@gmail.com'
 //  }
 //  stage('Slack Notification'){
   //    slackSend baseUrl: 'https://hooks.slack.com/services/',
    //   channel: '#jenkins-pipeline-demo',
    //   color: 'good', 
    //   message: 'Welcome to Jenkins, Slack!', 
    //  teamDomain: 'javahomecloud',
    //   tokenCredentialId: 'slack-demo'
  }

}

