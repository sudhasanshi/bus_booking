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
                    sh 'mvn clean install'
                }
            }
        }
    }
}
