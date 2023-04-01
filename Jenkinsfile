pipeline {
    agent any
    stages {
        stage('git clone'){
            steps {
               git branch: 'main', url: 'https://github.com/Athira-krish/angular-pro.git'
            }
        }
      stage('build'){
            steps {
               nodejs(nodeJSInstallationName: 'Nodejs 19.8.1'){
               sh 'npm install'
               sh 'npm link @angular/cli'
               sh 'ng build'
               sh 'cp -R /var/lib/jenkins/workspace/angular/dist/zappy_boiler_plate/* /var/www/html/'
               }
            }
        }
    }  
}
