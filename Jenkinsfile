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
  }
  stage('Copy Artifacts')
  {
    steps
    {
      copyArtifacts filter:'/var/lib/jenkins/workspace/Package_Application_Code_Pipeline/target/*.jar', projectName: 'Package_Application_Code_Pipeline'
    }
  } 
}
}
