def imageName = 'grey-shirt/movies-loader'

node('workers'){
    stage('Checkout'){
        checkout scm
        }

    stage('Unit Tests'){
        def imageTest= docker.build("${imageName}-test",
        "-f Dockerfile.test .")
        sh "docker run --rm -v /app/reports:/app/reports grey-shirt/movies-loader-test ${imageName}-test"
        junit "/app/reports grey-shirt/movies-loader-test/*.xml"
    }
}