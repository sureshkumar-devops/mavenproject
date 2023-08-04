pipeline
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
  stage('Deploy to prod')
  {
    steps
    {
      deploy adapters: [tomcat9(credentialsId: 'tomcat-id', path: '', url: 'http://34.23.164.52:9090/')], contextPath: '/', war: '**/*.war'
    }
  }
 
}
}
