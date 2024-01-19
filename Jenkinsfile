pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the source code from version control
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build the Maven project
                sh 'mvn clean install'
            }
        }

        stage('Unit Tests') {
            steps {
                // Run unit tests
                sh 'mvn test'
            }
        }

        stage('Integration Tests') {
            steps {
                // Run integration tests
                sh 'mvn verify'
            }
        }

        stage('Deploy to Staging') {
            when {
                // Run this stage only if the branch is 'staging' and the build is successful
                expression { env.BRANCH_NAME == 'staging' && currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            }
            steps {
                // Deployment to staging environment
                sh './deploy-to-staging.sh'
            }
        }

        stage('Deploy to Production') {
            when {
                // Run this stage only if the branch is 'production' and the build is successful
                expression { env.BRANCH_NAME == 'production' && currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            }
            steps {
                // Deployment to production environment
                sh './deploy-to-production.sh'
            }
        }
    }

    post {
        success {
            // Additional steps to run on successful deployment
            echo 'Deployment successful!'
        }
        failure {
            // Additional steps to run on deployment failure
            echo 'Deployment failed!'
        }
    }
}
