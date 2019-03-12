pipeline {
    agent any
    stages {
        stage("Gather Deployment Parameters") {
            steps {
                timeout(time: 30, unit: 'SECONDS') {
                    script {
                        // Show the select input modal
                       def INPUT_PARAMS = input message: 'Please Provide Parameters', ok: 'Next',
                                        parameters: [
                                        choice(name: 'ENVIRONMENT', choices: ['dev','prod'].join('\n'), description: 'Please select the Environment'),
                                        choice(name: 'DEPLOY', choices: ['yes', 'no'], description: 'Deploy?')]
                        env.ENVIRONMENT = INPUT_PARAMS.ENVIRONMENT
                        env.IMAGE_TAG = INPUT_PARAMS.DEPLOY
                    }
                }
            }
        }
        stage("Use Deployment Parameters") {
         steps {
                script {
                    echo "All parameters have been set as Environment Variables"
                    echo "Selected Environment: ${env.ENVIRONMENT}"
                    echo "Selected Tag: ${env.DEPLOY}"
                }
         }
        }
    }
}
