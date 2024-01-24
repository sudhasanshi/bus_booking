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
    }
}
