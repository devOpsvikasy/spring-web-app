pipeline{
    agent any
    //environment  {
      //  PATH = "$PATH:/opt/apache-maven-3.8.2/bin"
    //}
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/devOpsvikasy/spring-web-app.git'
            }
         }        
       stage('Build & deploy'){
            steps{
                sh 'mvn deploy'
              //  sh 'mvn clean deploy -DskipTests -e'
            }
         }
       stage('SonarQube analysis') {
        //    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube') { 
        // If you have configured more than one global server connection, you can specify its name
        //      sh "${scannerHome}/bin/sonar-scanner"
        //sh "mvn sonar:sonar"
         sh 'mvn sonar:sonar'
                }
            }
        }
          
    }
}
