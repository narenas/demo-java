pipeline {
    agent any 
    tools {
        maven 'mvn-3.6.1'
    }
    stages {
        stage ('Build'){
            steps {
                echo  'echo Hello World'
                sh 'mvn package '
            }
        }
    }
}