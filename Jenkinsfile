pipeline {
   agent any

   stages {
      stage('build') {
         steps {
            sh '''mvn clean package'''
         }
      } 
      stage('test') {
         steps {
            echo 'Hello World'
         }
      }
      stage('deploy') {
         steps {
            sh 'docker rmi file2:1.0; docker build -t file2:1.0 .; docker tag file2:1.0 gaellesimo/file2:1.0; docker push gaellesimo/file2:1.0'
         }
      }
   }
}
