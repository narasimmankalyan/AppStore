pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }

    parameters {
        string(name: "Environment", defaultValue: "dev", description: "Deployment environment")
        choice(name: "Selection", choices: ["build", "test"], description: "Select action")
        booleanParam(name: "continue_build", defaultValue: false, description: "Do you want to continue?")
    }

    stages {

        stage("First Stage") {
            steps {
                script {
                    if (params.Environment == "dev") {
                        echo "First stage of scripts"
                    }
                }

                // Proper input step
                // input message: "Do you want to continue?"
            }
        }

        stage("Docker Login") {
            steps {
                sh """
                    echo "--------------- Logging into Docker Hub -----------"
                    echo \$DOCKERHUB_CREDENTIALS_PSW | docker login -u \$DOCKERHUB_CREDENTIALS_USR --password-stdin
                    echo "--------------- Successfully logged in -----------"
                """
            }
        }
                stage("Docker Build") {
            steps {
                sh """
                docker build -t test10 .

                """
            }
        }

        stage("Action Stage") {
            steps {
                script {
                    if (params.Selection == "build") {
                        echo "Running build process..."
                    } else if (params.Selection == "test") {
                        echo "Running test process..."
                    }

                    def result = test()
                    echo "Function Output: ${result}"
                }
            }
        }
    }
}

def test() {
    return "______final_value______"
}
