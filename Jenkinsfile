node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Compile-Package'){
      def mvnHome =  tool name: 'maven_3_5_0', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Testing Stage'){
      def mvnHome =  tool name: 'maven_3_5_0', type: 'maven'   
      sh "${mvnHome}/bin/mvn test"
   }
   stage('upload Artifact'){
      def uploadSpec = "central"{
  "files": [
    {
      "pattern": "/var/lib/jenkins/workspace/new-demo2/target/*myweb*.war",
      "target": "ci_demo"
    }
 ]
}"""
server.upload(uploadSpec)
   
}
