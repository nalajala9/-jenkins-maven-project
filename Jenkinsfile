pipeline {
    agent any
    tools{
        maven 'Maven' 
        jdk 'JDK' 
    }
    stages {
        stage('Build') {
            steps {
                sh 
            sh 'mvn clean package -Dmaven.test.skip=true' 
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
