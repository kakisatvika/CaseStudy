pipeline{
    agent any
    stages{
        stage ("Build Docker Image"){
            steps{
                echo "Build Docker Image"
                bat "docker build -t mywebapp:v1 ."
            }
        }
        stage ("Docker Login"){
            steps{
                bat "docker login -u kakisatvika -p Satvika@23"
            }
        }
        stage("push Docker Iamge to Docker Hub"){
            steps {
                echo "push Docker Image to docker hub"
                bat "docker tag mywebapp:v1 kakisatvika/casestudy:t1"
                bat "docker push kakisatvika/casestudy:t1"
            }
        }
        stage("Deploy to Kubernetes"){
            steps{
                bat "kubectl apply -f Deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml"
            }
        }
    }
    post{
        success{
            echo 'Pipeline completed scucessfull!'
        }
        failure{
            echo "Pipeline failed.Please check the logs."
        }
    }
}
