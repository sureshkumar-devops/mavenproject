pipeline
{
agent any
triggers
 pollSCM {'* * * * * '}
stages
{
  stage('Build Application')
  {
    steps
    {
      sh mvn -f pom.xml 'clean package'  
    }
    post
    {
        success
        {
            echo "Now Archiving the Artifacts...."
            archiveArtifacts artifacts: '**/*.war'
        }
    }
  }  
}
}
