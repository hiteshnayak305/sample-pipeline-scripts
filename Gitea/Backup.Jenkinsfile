pipeline {
 agent any

 parameters {
  string defaultValue: '/etc/gitea/app.ini', description: 'app.ini path', name: 'ini_config', trim: true
  string defaultValue: '/var/lib/gitea', description: 'gitea data path', name: 'data_path', trim: true
 }

 stages {
  stage('Prerequisite') {
   steps {
    sh "echo 'Creating gitea backup ...'"
    sh "sudo mkdir -p ${WORKSPACE_TMP}"
    sh "sudo mkdir -p ${WORKSPACE_TMP}/config/"
    sh "sudo mkdir -p ${WORKSPACE_TMP}/data/"
   }
  }
  stage('Dump') {
   steps {
    sh "sudo cp -f ${ini_config} ${WORKSPACE_TMP}/config/"
    sh "sudo cp -rf ${data_path} ${WORKSPACE_TMP}/data/"
    sh "sudo cd ${WORKSPACE_TMP}"
    sh "sudo zip -rq ${WORKSPACE}/gitea-\$(date '+%Y%m%d%H%M%S').zip *"
   }
  }
  stage('Cleanup') {
   steps {
    sh "sudo rm -rfd ${WORKSPACE_TMP}"
    sh "sudo --user=root --group=root chown -R jenkins:jenkins ${WORKSPACE}"
    sh "echo 'Finished gitea backup.'"
   }
  }
 }
}