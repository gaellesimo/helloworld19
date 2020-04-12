pipeline {
    agent any
    tools {
        maven 'M2_HOME'
      
    }
    stages {
      stage('Build'){
        steps {
          echo "Build step"
          sh 'mvn clean'
          sh 'mvn install'
          sh 'mvn package'
        }
      
      
      }
        stage('test '){
        steps {
          echo "test step"
          sh 'mvn test'
        }
      
      
      }
        stage('deploy'){
        steps {
         sshPublisher(publishers: [sshPublisherDesc(configName: '34.204.179.45', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'docker rmi podieu:v.${BUILD_NUMBER}; docker build -t podieu:v.${BUILD_NUMBER} .; docker tag podieu:v.${BUILD_NUMBER} gaellesimo/podieu:v.${BUILD_NUMBER}; docker push gaellesimo/podieu:v.${BUILD_NUMBER};', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'webapp/target', sourceFiles: '**/*.war')], usePromotion
