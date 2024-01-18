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
        sh '${MAVEN_HOME}/bin/mvn clean package'
      }
    }
    stage('Run Locally') {
      steps {
        sh '${MAVEN_HOME}/bin/mvn clean package'
        sh 'java -jar target/bus-booking.jar &'
          sleep 30
      }
    }
     stage('deploy') {
      steps {
        sh 'ssh root@172.31.3.184'
        sh 'scp /home/king/workspace/bus-booking-pipeline/target/bus-booking-app-1.0-SNAPSHOT.jar  root@172.31.3.184:/opt/apache-tomcat-8.5.98/webapps/'
        sh 'echo "launching application"'
      }
    }
  }
}
