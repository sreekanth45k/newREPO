node{
     
    stage('Git Clone') {
        
         git url: 'https://github.com/sreekanth45k/newREPO.git',branch: 'master'
    }
    
    stage('Mvn Package'){
      def mvnHOME = tool name: 'Maven', type: 'maven'
      def mvnCMD = "${mvnHOME}/bin/mvn"
      sh "${mvnCMD} clean package"
      
    } 
    
    
    stage('Build Docker Image'){
        sh 'docker build -t sreekanth45k/java-web-app .'
    }
    
    stage('Push Docker Image'){
        withCredentials([string(credentialsId: 'sreekanth45k', variable: 'sreekanth45k')]) {
          sh "docker login -u sreekanth45k -p ${sreekanth45k}"
    }
        sh 'docker push sreekanth45k/java-web-app'
     }
     
}
