node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Compile-Package'){
      def mvnHome =  tool name: 'maven_3_5_0', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Deploy to Tomcat'){
      sshagent(['tomcat-dev']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war' ci_tomcate@35.231.153.198:/var/lib/tomcat/webapps'
      }
   }
}
