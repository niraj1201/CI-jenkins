node{
      stage('Mvn Package'){
	  def mvnHome = tool name: 'maven_3_5_0', type: 'maven'
	  def mvnCMD = "${mvnHome}"/bin/mvn"
	  sh "${mvnCMD} clean package"
	 }
}
