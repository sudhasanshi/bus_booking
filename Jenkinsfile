pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                sh 'rm -rf bus_booking'
                sh 'git clone https://github.com/sudhasanshi/bus_booking.git'
            }
        }

        stage('build') {
            steps {
                script {
                    sh 'sudo apt update'
                    sh 'sudo apt install maven'
                    sh 'mvn clean install'
                }
            }
        }
    }
}
