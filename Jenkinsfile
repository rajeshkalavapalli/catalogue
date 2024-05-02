pipeline{
    agent {
        node {
            label 'AGENT'
            
        }
}
    environment { 
        packageVersion = ''
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
       
        stage ('get version ') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "applictaion version: $packageVersion"
                }
            }
        }
        
        stage ('install dependencies') {
            steps {
                sh """
                    npm install 
                
                """
            }
        }
        
        stage ('build') {
            steps {
                sh """
                    ls -la
                    zip -r catalogue.zip ./* -x ".git"^Cx "*.zip"
                    ls -ltr
                
                """
            }
        }
    }
    post { 
        always { 
            echo 'I will always exicute run !'
            deleteDir()
        }
        failure { 
            echo 'I will always run when failure !'
        }
        success { 
            echo 'I will always run when success !'
        }
    }
}

