pipeline {
 agent none

 triggers{ cron('@daily') }

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
