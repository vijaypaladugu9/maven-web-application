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
             sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@52.209.36.144:/opt/apache-tomcat-9.0.58/webapps'
} 
}
}
}
}
