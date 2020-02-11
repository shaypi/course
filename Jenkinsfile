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
    }
}

