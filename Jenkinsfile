def imageName = 'grey-shirt/movies-loader'

node('workers'){
    stage('Checkout'){
        checkout scm
        }

    stage('Unit Tests'){
        def imageTest= docker.build("${imageName}-test",
        "-f Dockerfile.test .")
        sh "docker run --rm -v \$(pwd)/reports:/app/reports ${imageName}-test"
        junit allowEmptyResults: true, testResults: "\$(pwd)/reports/*.xml"
    }
}