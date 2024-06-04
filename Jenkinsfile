pipeline {
    agent {
        node {
            label 'maven-agent'
        }
    }

    environment {
    PATH = "/usr/share/maven/bin:$PATH"
}
    stages {
        stage('build'){
            steps {
                sh 'mvn clean deploy'
            }
        }
        stage('SonarQube analysis') {
            environment {
            scannerHome = tool 'rtv-SonarScanner'
            }
        steps { 
            
        withSonarQubeEnv('rtv-SonarQube-Server') { // If you have configured more than one global server connection, you can specify its name
            sh "${scannerHome}/bin/sonar-scanner"
    }
    }
}
    }}

