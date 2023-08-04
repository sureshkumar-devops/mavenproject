wpipeline
{
agent any
triggers
{
 pollSCM '* * * * *'
}
stages
{
  stage('Build')
  {
    steps
    {
        sh 'mvn -f pom.xml clean package'
    }
    post
    {
      success
      {
      echo 'Package of Artifacts...'
      archiveArtifacts artifacts: '**/*.war'
      }
    }
  }
  stage('Deploy to Staging Env')
  {
    steps
    {
      copyArtifacts filter: '**/*.war', projectName: 'Package_Application_Code_Pipeline'
    }
  }
 
}
}
