pipeline {
 agent any

 stages {
  stage('Cleanup') {
   steps {
    sh """
        cd /var/lib/jenkins/plugins
        rm -f *.bak
    """
    sh "echo 'Finished cleaning'"
   }
  }
 }
}