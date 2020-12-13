pipeline {
  agent any
  stages {
    stage('First') {
      steps {
        sh ' echo "Step First" '
        script {
			    env.EXECUTE="TRUE"
		    }

      }
    }

    stage('Second') {
      when {
                branch 'main'
                anyOf {
                    environment name: 'EXECUTE', value: 'TRUE'
                }
            }
      steps {
        sh ' echo "Updating Second Stage" '
      }
    }

    stage('Third') {
       when {
                branch 'main'
                anyOf {
                    environment name: 'EXECUTE', value: 'FALSE'
                }
            }
      steps {
        sh ' echo "Updating Third Stage" '
      }
    }

  }
}
