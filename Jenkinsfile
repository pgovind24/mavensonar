pipeline {
 agent any
	tools {
        maven 'mymaven' 
    }
	 stages {
    stage('Analysis') {
	 steps {
              withSonarQubeEnv('SonarQube') {
                sh 'mvn  sonar:sonar'
              }
              echo "Analysis"
            }
	 }
	  stage("Quality Gate") {
            steps {
              timeout(time: 5, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
              echo "quality passed"
            }
          }
}
}
    
