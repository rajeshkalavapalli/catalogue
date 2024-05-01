pipeline{
    agent {
        node {
            label 'AGENT-1'
            
        }
}
    environment { 
        PackageVersion = ''
    }

    options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()
    }
    // parameters {
    //     string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }

    stages {
       
        stage ('get the version') {
            steps {
                script{
                    def PackageJson = readJSON file: 'Package.json'
                    PackageVersion = PackageJson.version
                    echo "application version :$packageVersion"
                }
            }
        }
        stage ('build') {
            steps {
                echo 'build.......'
            }
        }
        stage ('deploye') {
            steps {
                sh """
                    echo 'iam learning jenkins.......'
                    echo '$GREETING'
                """
            }
        }

    }   
    post { 
        always { 
            echo 'I will always exicute run !'
        }
        failure { 
            echo 'I will always run when failure !'
        }
        success { 
            echo 'I will always run when success !'
        }
    }
}


