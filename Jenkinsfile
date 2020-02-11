pipeline{
    agent any
    tools{
    maven 'M3'
    }
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }

    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/shaypi/course'
            }
        }
        stage("Maven Build"){
            steps{
                sh 'mvn -B -DskipTests clean package'
                sh "mvn clean package"
                sh 'mvn package'
            }                
        }
        stage('Build && SonarQube analysis') {
                withSonarQubeEnv('sonarqube') {
                    container('maven') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
        }
    }
}

