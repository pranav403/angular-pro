pipeline {
    agent any

    stages {
        stage('Git Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/pranav403/angular-pro.git'
            }
        }
        stage('build') {
            steps {
                nodejs(nodeJSInstallationName: 'angular'){
                    sh 'npm install'
                    sh 'npm link @angular/cli'
                    sh 'ng build'
                }    
            }
        }
        stage('aws log') {
            steps {
                withCredentials([[
                $class: 'AmazonWebServicesCredentialsBinding',
                credentialsId: 'aws',
                accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                {
                    sh 'aws s3 cp /var/lib/jenkins/workspace/angular/dist/zappy_boiler_plate/ s3://angular-qwertyuiop --recursive'
                }
            }
        }
    }
}
