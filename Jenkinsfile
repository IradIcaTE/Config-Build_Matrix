pipeline {
    agent { label "First" }

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Select the environment to deploy to')
        booleanParam(name: 'RUN_TEST', defaultValue: true, description: 'Run unit tests before deployment')
    }

    stages {
        stage("Initialize") {
            steps {
                echo "Environment selected: ${params.ENVIRONMENT}"
                echo "Run Tests: ${params.RUN_TESTS}"
            }
        }

        stage("Run Tests") {
            when {
                expression { return params.RUN_TESTS }
            }
            steps {
                echo "Executing unit tests for ${params.ENVIRONMENT}..."
                sh "echo '[Mock Test] All tests passed in ${params.ENVIRONMENT}'"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENVIRONMENT} environment..."
                sh "echo '[MOCK DEPLOY] deployment to ${params.ENVIRONMENT} complete!'"
            }
        }
    }
}