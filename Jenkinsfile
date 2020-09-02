pipeline {
    agent any
    tools {
        maven 'M2_HOME'   
    }
    triggers {
  pollSCM '* * * * *'
}
   
    stages {
        
        stage('build') {
            steps {
                echo 'Hello World'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'
                
            }
        }
        stage('build and publish image') {
      steps {
        script {
          checkout scm
          docker.withRegistry('', 'DockerRegistryID') {
          def customImage = docker.build("olive123/hol-pipeline:${env.BUILD_ID}")         
          def customImage1 = docker.build("olive123/hol-pipeline")
	      customImage.push() 
	      customImage1.push()
          }
    }
        
    }
}
           stage ( 'deployment trigger'){
              steps {
	        build 'hol-CD'
} 
}
    }
}
