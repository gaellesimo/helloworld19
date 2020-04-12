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
         sshPublisher(publishers: [sshPublisherDesc(configName: 'ec2-user@34.204.179.45', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'docker  rmi podieu-ewr-app:1.0 ; docker build -t  podieu-ewr-app:1.0 . ; docker tag podieu-ewr-app:1.0  gaellesimo/podieu-ewr-app:1.0; docker push  gaellesimo/podieu-ewr-app:1.0', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', remoteDirectorySDF: false, removePrefix: '**/*.war', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        }
            
      }     
    }
}
