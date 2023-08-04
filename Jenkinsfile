pipeline
{
agent any
triggers
{
 pollSCM '* * * * *'
}
stages
{
  stage("Git Checkout")
  {
      steps{
            git 'https://github.com/sureshkumar-devops/mavenproject.git'
           }
  }
  stage('Build')
  {
    steps
    {
        sh 'mvn -f pom.xml clean package'
        archiveArtifacts artifacts: '**/*.war', caseSensitive: false, onlyIfSuccessful: true
    }    
  }
  stage('Copy Artifacts')
  {
    steps
    {
      copyArtifacts filter:'**/*.jar', projectName: 'Package_Application_Code_Pipeline'
    }
  } 
}
}
