pipeline{
    agent any

    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/shaypi/course'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh 'mvn package'
            }                
        }
    }
}
