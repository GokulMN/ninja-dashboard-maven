pipeline {
 agent any
stages {
 stage('CodeCheckout') {
 steps {
 script {
    checkout scm

     sh 'apt-get install -y default-jdk'
     sh 'sudo apt install -y maven'
  
     }
    }
   }
   
 stage('build customer app code') { 
 steps {
  script {
    
        sh 'sudo apt install -y maven'
        sh 'mvn clean install'
    }
  }
 }
 
  stage('docker images code') { 
 steps {
  script {
       sh 'docker build -t rakeshraheja89/project .'
       sh 'docker container run -d -p 3001:8080 -v  /var/run/docker.sock:/var/run/docker.sock rakeshraheja89/project'
        sh 'sudo apt install -y maven'
        sh 'mvn clean install'
    }
  }
 }
}
}
