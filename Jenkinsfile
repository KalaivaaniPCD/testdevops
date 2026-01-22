pipeline {
agent any
triggers {
githubPush()}
stages {
stage('Checkout') {
steps {
checkout scm
}
}
stage('Build') {
when {
branch 'develop'
}
steps {
sh 'mvn clean compile'
}
}
stage('Test') {
steps {
sh 'mvn test'
}
}
stage('Package') {
when {
anyOf {
branch 'release/*'
branch 'main'
}}
steps {
sh 'mvn clean package'
}
}
}
post {
success {
echo 'CI Pipeline executed successfully'
}
failure {
echo 'CI Pipeline failed'
}
}
}
