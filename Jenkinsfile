pipeline {
    agent any
    tools{
        maven 'Maven' 
        jdk 'JDK 1.8.*' 
    }
    
    
    stages {
        
        stage('Build') {
            steps {
            sh 'mvn -f hello-app/pom.xml clean package -Dmaven.test.skip=true' 
            sh  "ls -al"
            }
            post {
                success {
                    echo "Now Archiving the Artifacts....."
                    archiveArtifacts artifacts: '**/*.jar'
                    sh 'ls -al'
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
