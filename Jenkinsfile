pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('git checkout'){
            steps{
              git 'https://github.com/vijaypaladugu9/maven-web-application.git'   
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
     stage('publish to nexus'){
            steps{
              sh 'mvn clean package'  
}
}
         stage('deploy to tomcat'){
            steps{
             sshagent(['qa']) {
             sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@34.248.112.229:/opt/tomcat/webapps'
} 
}
}
}
}
