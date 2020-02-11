pipeline{
    agent any

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
        stage('Build && SonarQube analysis'){
            steps{
                withSonarQubeEnv('sonarqube'){
                    container('maven') {
                        sh 'mvn clean package sonar:sonar'
                    }
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
