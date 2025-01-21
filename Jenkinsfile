node {
    def app
    stage('Clone repository') {
        git 'https://github.com/bbangwon/fork_vs_vfork.git'
    }
    stage('Build image') {
        app = docker.build("cyi38317/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
