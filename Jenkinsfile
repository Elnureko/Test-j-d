pipeline {
    agent { label 'Linux' }
    stages {
        stage('downloading repo from github') {
            steps {
                echo "Downloading Repo"
                git branch: 'main', url: 'https://github.com/Elnureko/Test-j-d.git'
                sh 'echo second step'
                sh 'sleep 1'
                sh '''
                echo 'working on'
                echo 'slave node'
                '''
            }
        }
        stage('Creating Docker Image') {
            steps {
                echo "Creating docker image from Dockerfile"
                sh 'docker build -t eko/test_app:1.0 .'
         
            }
        }
        stage('Pushing Docker Image Into Official Docker Repository') {
            steps {
                echo "Creating docker image from Dockerfile"
                sh 'docker login -u elanveyila -p Mira2019.'
                sh 'docker push eko/test_app:1.0'
                sh 'echo "pushing image is finished"'
            }
        }

        stage('Running Docker Image as Container') {
            steps {
                echo "Running Docker Image as Container"
                sh 'docker run -dit -p 80:80 eko/test_app:1.0'
                sh 'echo "Application is running at port:80"'
            }
        }
    }
}
