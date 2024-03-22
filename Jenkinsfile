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
            }
        }
        stage('Environment Set-up') {
            steps {
                sh '#!/bin/bash'
                sh 'rm -rf env'
                sh 'ls'
                sh 'python3 -m venv env && . env/bin/activate'
                sh 'pip install pytest'
                sh 'python3 ./sources/add2vals.py'
            }
        }
        stage('Test') {
            steps {
                sh 'py.test --junit-xml test-reports/results.xml sources/test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
    }
}