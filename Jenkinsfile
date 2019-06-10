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
        stage ('Deploy') {
            steps {
                echo 'Deploying'
                sh 'mvn deploy:deploy-file -DgeneratePom=false DrepositoryId=releases -Durl=http://nexus:8081/nexus/content/repositories/releases/ -DpomFile=pom.xml -Dfile=target/demo.war'
            }
        }
    }
}