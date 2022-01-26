pipeline{
agent any
tools{
    maven 'maven'
}
stages{
  stage('code checkout'){
    steps{
         git 'https://github.com/sharathdevops5/maven-web-application.git'
    }
    }
    stage('sonar analysis'){
    steps{
         sh 'mvn sonar:sonar'
    }
    }
     stage('build war'){
    steps{
         sh 'mvn clean package'
    }
    }
     stage('publish war'){
    steps{
         sh 'mvn deploy'
    }
    }
     stage('deploy to tomcat'){
    steps{
        sshagent(['tomcatssh']) {
    sh 'scp -o StrictHostKeyChecking=no target.war ec2-user@34.228.170.18optapache-tomcat-9.0.58webapps/'
}
    }
    }
}
}
