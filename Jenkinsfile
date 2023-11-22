pipeline {
  agent any 
  parameters{
    choice(name:'ENVIRONMENT',choices:['QA','Production'],description:'Select deployment environment')    
  }
  stages {
    stage("Build"){
      steps{
        echo 'building the application ...'
      }
    }
     stage("Test"){
      steps{
          echo 'testing the application ...'
      }
    }
     stage("Deploy to QA"){
       when {
         expression{
           params.ENVIRONMENT =='QA'}
       }
      steps{
          echo 'Deploying the application to QA...'
      }
    }
    stage("Deploy to production "){
       when {
         expression{
           params.ENVIRONMENT =='Production'}
       }
      steps{
          echo 'Deploying the application to production ...'
      }
    }
    stage("Final Approval"){
       when {
         expression{
           params.ENVIRONMENT =='QA'}
       }
      steps{
          echo 'Do you want to deploy the application to production?'
      }
    }
    stage("Deploy to production(Final) "){
       when {
         expression{
           params.ENVIRONMENT =='QA'}
         beforeAgent true
       }
      steps{
          echo 'Deploying the application to production final ...'
      }
    }
      }
  post{
    success{
      echo "pipeline completed successfully"
    }
    failure{
      echo "pipeline failed"
    }}
}
