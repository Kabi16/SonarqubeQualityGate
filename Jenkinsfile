pipeline {
    agent any

    tools {
     maven 'Maven3'
    }
  
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '50f6fddf-d641-43aa-ac88-881339c4ed19', url: 'https://github.com/Kabi16/SonarqubeQualityGate.git']]])
            }
        }
        
       stage ('Build') {
         steps {
              bat 'mvn clean install -f MyWebApp/pom.xml'
            }
        }
        
        stage ('Code Quality') {
        steps {
            withSonarQubeEnv('SonarQube') {
            bat 'mvn -f MyWebApp/pom.xml sonar:sonar'
            }
      }
    }
    
