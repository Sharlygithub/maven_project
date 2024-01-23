pipeline {
    agent any

    tools {
        maven "mvn"
    }

    triggers {
        pollSCM('* * * * *') // Schedule SCM polling at a specified interval (every minute in this example)
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sharlygithub/maven_project.git'
            }
        }

        stage('Build') {
            steps {
                echo 'building the application'
            }
        }

        stage('Test') {
            steps {
                echo 'testing the application'
            }
        }

        stage('Deploy') {
            steps {
                echo 'deploying the application'
                // Add deployment commands or scripts here
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
            // Add additional success actions or notifications here
        }
        failure {
            echo 'Build or deployment failed!'
            // Add additional failure actions or notifications here
        }
    }
}
