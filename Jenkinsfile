properties([parameters([choice(choices: 'test\ndeploy', name: 'baranch')])])
pipeline {
  agent {
    label 'king'
  }
  stages {
    stage('checkout') {
      steps {
        sh 'rm -rf  bus_booking'
        sh 'git clone https://github.com/sudhasanshi/bus_booking.git'
      }
    }
    stage('build') {
      steps {
        sh 'mvn --version'
        sh 'mvn clean install'
      }
    }
  }
}
