pipeline {
    agent any 
    tools {
        maven 'mvn-3.6.1'
    }
    environment {
        USER_CREDS = credentials('maven-nexus-creds')
    }
    stages {
        stage ('Build'){
            steps {
                echo  'echo Hello World'
                sh 'mvn package'
            }
        }
        stage ('QA') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
        stage ('Deploy') {
            steps {
                echo 'Deploying'
                sh 'mvn -X deploy:deploy-file -DgeneratePom=false -DrepositoryId=nexus -Durl=http://nexus:8081/repository/devel-snapshot/ -DpomFile=pom.xml -Dfile=target/demo.war'
            }
        }
    }
}