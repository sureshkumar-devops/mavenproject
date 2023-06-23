pipeline{

agent any
stages{
   stage('Build Application'){
      steps{
        sh 'mvn clean package'
      }
      posts{

        success{

            echo "Now Archiving the Artifacts...!"
            archiveArtifacts artifacts: '**/*.war'
        }
      }

   }

}

}