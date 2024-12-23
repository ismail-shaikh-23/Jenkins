pipeline {
    agent any

    environment {
        name = "ismail"
    }

    parameters {
        string(name: "Person", defaultValue: "ismail shaikh")
        choice(name: "city", choices: ["mumbai", "pune", "chennai"])
    }

    stages {
        stage("environment") {
            steps {
                echo "${name}"
            }
        }



        stage("parameter") {
            steps {
                echo "${Person}"
                echo "${city}"
            }
        }

        stage("test") {
            steps {
                echo "this is test stage"
                sh ''' 
                if [ ! -d test ]; then
                    mkdir test
                    echo "Directory 'test' created"
                else
                    echo "Directory 'test' is already present"
                fi
                '''
            }
        }

        stage("build") {
            steps {
                echo "this is build"
                sh '''
                    ls
                    pwd
                '''
            }
        }

        stage("continue ?") {
            steps {
                input message: "Should we continue?", ok: "Yes"
                echo "Deploying..."
            }
        }

        stage("deploy") {
            environment {
                last = "shaikh"
            }
            steps {
                echo "This is deploy"
                echo "Last name: ${last}"
                sh "touch deploy.txt"
            }
        }
    }
    post{
        always{
            echo "always execute"
        }
        failure{
            echo "only fail"
        }
        success{
            echo "only sucsess"
        }
    }
}
