pipeline {
    options
    {
        buildDiscarder(logRotator(numToKeepStr: '20'))
    }
    environment 
    {        
       


    }
   
  stages {
    stage('Checkout') {
      steps {   
        checkout scm
      }
    }

   
   

      stage ('Run devportal automated testplans') {
      steps{
      build job: 'kongtemplate_job', propagate: true
        }
    }
     

    stage('Clean up') {
      steps {
        deleteDir()
        script {
          currentBuild.result = 'SUCCESS'
        }

      }
    }
  }
  post {
    failure {
      script {
        currentBuild.result = 'FAILURE'
      }
    }
  }
}
