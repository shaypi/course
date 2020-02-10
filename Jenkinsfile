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
            def mvn_version = 'M3'
            steps{
                withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
              //sh "mvn clean package"
                sh 'mvn package'
            }                
        }
    }
}

