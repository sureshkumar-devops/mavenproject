pipeline{
    agent any
    stages{
        stage('Build Application'){
            steps{
                sh 'mvn -f mavenproject/pom.xml clean package'
            }
        post{
        success{

            echo "Now Archiving the Artifacts...!"
            archiveArtifacts artifacts: '**/*.war'
        }
      }
   }
}
}