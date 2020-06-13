pipeline {
 agent none

 stages {
  stage('Dump') {
   steps {
    build job: 'Gitea/Dump'
   }
  }
  stage('Backup') {
   steps {
    build job: 'Gitea/Backup'
   }
  }
 }
}
