pipeline {
    agent any
     triggers {
  triggers {
  pollSCM '''H/10 * * * * 
'''
}

 tools {
        maven 'M2_HOME'   
    }
   
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
          def customImage = docker.build("olive123/hol-pipeline:${env.BUILD_ID}")         def customImage = docker.build("olive123/hol-pipeline")
	  customImage.push() 
	  customImage1.push()
          }
    }
        
    }
}
  }
}
