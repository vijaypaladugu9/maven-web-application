
pipeline{
agent any
tools{
    maven 'maven'
}

stages{
  stage('git checkout'){
     steps{
        git 'https://github.com/mahesh331/maven-web-application.git'
     }
  } 
  stage('sonar'){
     steps{
       sh 'mvn sonar:sonar'
     }
  }  
  stage('build'){
     steps{
       sh 'mvn clean package'
     }
  }   
  stage('nexus'){
     steps{
       sh 'mvn deploy'
     }
  }  
   stage('deploy'){
     steps{
       sshagent(['tomcat_credentials_new']) {
    sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@18.118.134.113:/opt/apache-tomcat-9.0.56/webapps/'
}
     }
  }    
}
}
