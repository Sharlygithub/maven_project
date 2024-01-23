pipeline { 
    agent any tools {
maven "mvn"
}
triggers {
pollSCM('* * * * *') // Schedule SCM polling at a specified interval (every minute in this example)
}
stages { 
    stage('Checkout') { 
        steps {
git branch: 'main', url: 'https://github.com/iamkishore0/maven_project.git'
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
}
}
}

post {
success {
echo 'Build and deployment successful!'
}
failure {
echo 'Build or deployment failed!'
}
}
}
