pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'javac marksCalculator.java'
                    } else {
                        bat 'javac marksCalculator.java'
                    }
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'java marksCalculator'
                    } else {
                        bat 'java marksCalculator'
                    }
                }
            }
        }
    }

    post {
        cleanup {
            script {
                if (isUnix()) {
                    sh 'rm -f *.class'
                } else {
                    bat 'if exist *.class del /q *.class'
                }
            }
        }
    }
}
