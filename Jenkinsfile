pipeline {
    agent any
    tools{
        maven 'Maven' 
        jdk 'JDK 1.8.*' 
    }
    
    stages {
        stage('git checkout'){
            steps{
                git branch: 'master',
                credentialsId: 'git_hub',
                url: 'https://github.com/nalajala9/-jenkins-maven-project.git'
            sh "ls -la"
            }
        stage('Build') {
            steps {
                sh 
            sh 'mvn -f hello-app/pom.xml clean package -Dmaven.test.skip=true' 
            sh  "ls -al"
            }
            post {
                success {
                    echo "Now Archiving the Artifacts....."
                    archiveArtifacts artifacts: '**/*.jar'
                }
            }
        }
        stage('Test') {
            steps {
                sh 'mvn -f hello-app/pom.xml test'
            }
            post {
                always {
                    junit 'hello-app/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
