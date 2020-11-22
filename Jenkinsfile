pipeline {

    agent any

    environment {
        FAVOURITE_FRUIT = 'tomato'
    }

    stages {
        stage('echo env vars') {

            steps {
                // This prints out all environment variables, sorted alphabetically
                // You should see the variables declared further below
                sh 'printenv | sort'

                sh "echo I like to eat ${FAVOURITE_EGG_TYPE} eggs"
                sh "echo And I like to drink ${FAVOURITE_DRINK}"
                sh "echo My favourite city is ${FAVOURITE_CITY}"

                // Build Parameters are also set as environment variables in the shell.
                sh "echo The worst GoT character is: ${WORST_THRONES_CHARACTER}"

                // We can also access some of the built-in environment variables
                sh "echo My hostname is: ${HOSTNAME}"

                // Environment variables can be overridden within a certain block
                withEnv(['FAVOURITE_CITY=Portland']) {
                    sh "echo My favourite city is temporarily ${FAVOURITE_CITY}"
                }
            }

            // This block is evaluated before executing the steps block
            environment {
                FAVOURITE_EGG_TYPE = "poached"
                FAVOURITE_DRINK = "sauvignon blanc"
                FAVOURITE_CITY = "London"
                FAVOURITE_FRUIT = "satsuma"
            }
        }

        stage('second stage') {
            steps {
                // This will echo tomato, because the env var was set at the global scope
                sh 'echo My favourite fruit is ${FAVOURITE_FRUIT}'
            }
        }

    }

}
