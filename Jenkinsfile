node{
  def app
    stage('Clone') {
        checkout scm
    }
    stage('Build image') {
        sh 'docker build ikrame/nginx .'
    }
    stage('Run image') {
        docker.image('ikrame/nginx').withRun('-p 80:80') { c ->
        sh 'docker ps'
        }
    }
}
