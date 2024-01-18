properties([parameters([choice(choices: 'test\ndeploy', name: 'baranch')])])
pipeline {
  agent {
    label 'king'
  }
  stages {
    stage('checkout') {
      steps {
        sh 'rm -rf  hello-world-war'
        sh 'git clone https://github.com/sudhasanshi/hello-world-war.git'
      }
    }
    stage('build') {
      steps {
        sh 'mvn --version'
        sh 'mvn clean install'
      }
    }
     stage('deploy') {
      steps {
        sh 'ssh root@172.31.3.184'
        sh 'scp /home/king/workspace/samplepipeline/target/hello-world-war-1.0.0.war  root@172.31.3.184:/opt/apache-tomcat-8.5.98/webapps/'
        sh 'echo "launching application"'
      }
    }
  }
}
