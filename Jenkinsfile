pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
           git branch: 'master', url: 'https://github.com/C180596/docker.git'
           }
        }
        
        stage ('docker login') {
            steps {
                 sh 'echo dckr_pat_eHv3A-hnkhtzzv3b90VYAtk5HGo | /usr/bin/docker login -u swapnilnagare17 --password-stdin'
            }
        
        }
        stage ('docker build image'){
            steps {
                 sh '/usr/bin/docker image build -t swapnilnagare17/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                 sh '/usr/bin/docker image push swapnilnagare17/mywebsite '
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9092:80 --replicas 5 swapnilnagare17/mywebsite'
            }
        }
    }
}
