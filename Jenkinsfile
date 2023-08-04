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
  stage('Copy Artifacts')
  {
    steps
    {
      copyArtifacts: '**/*.war'
    }
  }
  stage('Deploy to prod')
  {
    steps
    {
      deploy adapters: [tomcat9(credentialsId: 'tomcat-id', path: '', url: 'http://34.23.164.52:9090/')], contextPath: '/', war: '**/*.war'
    }
  }
