pipeline {
 agent any

 parameters {
  string defaultValue: '/etc/gitea/app.ini', description: 'app.ini path', name: 'ini_config', trim: true
 }

 stages {
  stage('Prerequisite') {
   steps {
    sh "echo 'Creating gitea dump ...'"
    sh "sudo --user=root --group=root chown -R gitea:gitea ${WORKSPACE}"
   }
  }
  stage('Dump') {
   steps {
    sh "sudo --user=gitea --group=gitea gitea dump -c ${ini_config} --tempdir=${WORKSPACE}"
   }
  }
  stage('Cleanup') {
   steps {
    sh "sudo --user=root --group=root chown -R jenkins:jenkins ${WORKSPACE}"
    sh "echo 'Finished gitea dump.'"
   }
  }
 }
}