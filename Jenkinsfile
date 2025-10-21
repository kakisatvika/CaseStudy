pipeline{
	agent any
	stages{
	stage('checkout'){
	steps{
	echo "Cloning repo"
	git url:"https://github.com/kakisatvika/CaseStudy.git",
	branch:'main'
	}
	}
	stage('Build'){
	steps{
	echo "Build Docker Image"
	bat "docker build -t mywebapp ."
	}
	}
	stage('Run'){
	steps{
	echo "Run application in Docker Container"
	bat "docker rm -f mycontainer || exit 0"
	bat "docker run -d -p 5000:5000 --name mycontainer mywebapp"
	}
	}
	}
	post{
	success{
	echo 'Pipeline finished successfully!'
	}
	failure{
	echo 'Pipeline failed.Please check the logs'
	}
	
	}
}