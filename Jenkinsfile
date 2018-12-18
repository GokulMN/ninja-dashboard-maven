pipeline {
 agent any
stages {
 stage('CodeCheckout') {
 steps {
 script {
    checkout scm  
     }
    }
   }
   
stage('build customer app code') { 
 steps {
  script {
   echo "Installing Java"
                sh 'sudo apt-get install -y default-jdk'
               
                    echo "Installing Maven"
                sh 'sudo apt-get -y install maven'
                sh 'mvn -B -DskipTests clean package'
        sh 'mvn clean install'
    }
  }
 }
 
  stage('docker images code') { 
 steps {
  script {
       sh 'docker build -t rakeshraheja89/project .'
       sh "docker login -u=$env.user -p=$env.password"
        sh "docker push rakeshraheja89/project"
         sh  'docker run -p 8090:8080 -d rakeshraheja89/project'
        
    }
  }
 }
}
}
