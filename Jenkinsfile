pipeline{
    agent any

    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }

    stages{
        stage("Git Checkout"){
            steps{
                cleanWs()
                git 'https://github.com/shaypi/course'
            }
        }                

        stage('Build && SonarQube analysis'){
            steps{
                withSonarQubeEnv('sonarqube'){
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
        stage('Upload war file'){
            steps{
                nexusArtifactUploader(
                                nexusVersion: 'nexus3',
                                protocol: 'http',
                                nexusUrl: 'nexus:8081',
                                version: '0.3.1',
                                groupId: 'time-tracker-web',
                                repository: 'maven-private',
                                credentialsId: 'nexus-creds',
                                artifacts: [
                                    [artifactId: 'time-tracker-web',
                                    file: 'web/target/time-tracker-web-0.3.1.war',
                                    type: 'war']
                                ]
                            );
            }
        }
    }
}
