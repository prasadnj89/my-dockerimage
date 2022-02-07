node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
        sh 'echo "Test Build"'
       app = docker.build("prasadnj89/my-dockerimage/Dockerfile")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://106209456475.dkr.ecr.ap-south-1.amazonaws.com/myfirst', 'git', registryCredentialsId 'aws_prasadnj') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
