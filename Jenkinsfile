node {
    def registryProjet='registry.gitlab.com/ikrameben/presentation-jenkins'
    def IMAGE="${registryProjet}:version-${env.BUILD_ID}"
    
   stage('clone') {
                checkout scm
   }
   
   def img = stage('Build') {
         docker.build("$IMAGE", '.')
   }
   
   stage('Run') {
         img.withRun("--name run-$BUILD_ID -p 81:81") { c ->
           sh 'curl localhost'
        }
   }
   
   stage('Push') {
        docker.withRegistry('https://registry.gitlab.com', 'reg1') { 
        img.push 'latest'
        img.push()
	     
        }
   }
}
