pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rithvikshetty/simple-python-pyinstaller-app/']]])
            }
        }
        stage('Build') {
            steps {
                git branch: 'master', url: 'https://github.com/rithvikshetty/simple-python-pyinstaller-app/'
                sh 'python3 add2vals.py'
            }
        }
        // stage('Test') {
        //     steps {
        //         sh 'python3 -m pytest'
        //     }
        // }
    }
}