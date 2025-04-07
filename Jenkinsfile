pipeline {
    agent any
    stages {
        stage('Setup Ruby') {
            steps {
                sh '''
                    export PATH="$HOME/.rbenv/versions/3.2.2/bin:$PATH"
                    eval "$(rbenv init -)"
                    ruby -v
                    bundle install
                '''
            }
        }
        stage('Checkout') {
            steps {
                git 'https://github.com/jaydipVrinsoft/DemoCICDiOS.git'
            }
        }
        stage('Install Dependecies') {
            steps {
                sh 'bundle install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'bundle exec fastlane test'
            }
        }
        stage('Build and Deploy') {
            steps {
                sh 'bundle exec fastlane deploy'
            }
        }
    }
}