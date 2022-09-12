pipeline{
    agent any
    //environment {
      //  PATH = "$PATH:/opt/apache-maven-3.8.2/bin"
    //}
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/Sharath8000/hello-world.git'
            }
         }        
       stage('Build & deploy'){
            steps{
                sh 'mvn clean deploy -X'
            }
         }
        stage('SonarQube analysis') {
        //    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube') { 
        // If you have configured more than one global server connection, you can specify its name
        //      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
                }
            }
        }
          
    }
}
