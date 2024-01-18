node{
  def app
    stage('Clone') {
        checkout scm
    }
    stage('Build image') {
        app = docker.build("ikrame/nginx")
    }
    stage('Run image') {
        docker.image('ikrame/nginx').withRun('-p 8001:81') { c ->
        sh 'docker ps'
        sh 'curl localhost'
        }
    }
}
