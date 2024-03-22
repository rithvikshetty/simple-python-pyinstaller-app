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
                sh """
                    ls
                    python3 -m venv env && . env/bin/activate
                    pip install -r requirements.txt
                """
            }
        }
        stage('Test') {
            steps {
                sh""" 
                . env/bin/activate
                pytest --junit-xml test-reports/results.xml sources/test_calc.py
                """
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
    }
}