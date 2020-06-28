pipeline
{
agent any
tools
{
  maven 'maven'
}
stages
{
  stage('checkout')
  {
    steps
    {
        checkout scm
     }
  }
  
  
  stage('Build')
  {
    steps
    {
      bat "mvn clean install"
    }
  }
	
  stage('Sonar Analysis')
  {
    steps
    {
      echo "Sonar"
      withSonarQubeEnv("local sonar") 
				{
					bat "mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar"
				}
    }
  }
	
    stage ('Uploading to Artifactory')
	{
		steps
		{
		echo "Stage for artifact"
		rtMavenDeployer (
                    id: 'deployer',
                    serverId: '123456789@artifactory',
		    snapshotRepo: 'devopsforqaRA',
                    releaseRepo: 'devopsforqaRA'
                    
                )
                rtMavenRun (
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: 'deployer',
                )
                rtPublishBuildInfo (
                    serverId: '123456789@artifactory',
                )
			
		}
	}
	
	stage('Docker Build Image')
	{
		steps
<<<<<<< HEAD
		{ 
		bat "docker build -t rahul/random-image ./
			
=======
		{
			bat "docker build -t rahul/random-image ./"
>>>>>>> b49434c3829d9bf193fe1740426a908ed9b63e7c
		}
	}
	
	stage('Docker Deployment-container run')
	{
		steps
		{
<<<<<<< HEAD
		bat "docker run -d -p 8081:8080 rahul/random-image"
			
=======
			bat "docker run -d -p 8081:8080 rahul/random-image"
>>>>>>> b49434c3829d9bf193fe1740426a908ed9b63e7c
		}
	}	
	
}
  
  }
