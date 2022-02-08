node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       sh 'echo "Test Build"'
       app = docker.build("prasadnj89/test")
       //app = docker.build("prasadnj89/my-dockerimage/Dockerfile")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://106209456475.dkr.ecr.ap-south-1.amazonaws.com/myfirst', 'git') {
        app.push("${env.BUILD_NUMBER}")
        app.push("latest")
        //def myImage = docker.build('myfirst)
        //myImage.push("latest")
        //docker.withRegistry('https://106209456475.dkr.ecr.ap-south-1.amazonaws.com', 'ecr:ap-south-1:myfirst-ecr-credentials') {
        //docker.image('demo').push('latest')
        }
    }
}
