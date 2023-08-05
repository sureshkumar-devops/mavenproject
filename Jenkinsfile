pipeline
{
 agent any
 triggers{ pollSCM '* * * * *' }
 stages
 {
  stage(.Checkout GitHub')
  {
    steps
    {
         git 'https://github.com/sureshkumar-devops/mavenproject.git'
    }
  }
  stage('Build')
  {
    steps
    {
        sh 'mvn -f pom.xml  clean package'
    }
  }
  stage('Archive Artifacts')
  {
   steps
   {
      archiveArtifacts artifacts: '**/*.war'
   }
  }
 }   
}
