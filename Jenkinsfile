node {
  def myGradleContainer = docker.image('gradle:jdk8')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     myGradleContainer.inside("-v jenkins_home/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && ./gradlew test'
     }
  }
  stage('run') {
     myGradleContainer.inside("-v jenkins_home/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && ./gradlew run'
     }
  }
}
