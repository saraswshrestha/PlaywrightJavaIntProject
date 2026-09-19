pipeline {

agent any

stages {

stage('Checkout') {
steps {
checkout scm
}
}

stage('Build Docker Image') {
steps {
bat 'docker build -t playwright-java:latest .'
}
}

stage('Run Tests in Docker') {
steps {
bat 'docker run --rm playwright-java:latest'
}
}
}

post {
always {
junit allowEmptyResults: true,
testResults: 'target/surefire-reports/*.xml'
}
}
}