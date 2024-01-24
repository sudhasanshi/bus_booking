pipeline {
    agent none
    stages {
        stage('checkout') {
            agent any
            steps {
                sh 'rm -rf bus_booking'
                sh 'git clone https://github.com/sudhasanshi/bus_booking.git'
            }
        }

        stage('build') {
            agent { label 'sudha' }
            steps {
                script {
                    sh 'mvn clean install'
                }
            }
        }
		 stage('deploy') {
		 agent { label 'sudha' }
            steps {
                sh "cp /home/sudha/workspace/bus-booking/target/bus-booking-app-1.0-SNAPSHOT.jar /opt/apache-tomcat-8.5.98/webapps/"
            }
        }
        
    }
    }
