node("docker") {
    docker.withRegistry('test', 'bindu29') {

        git url: "https://github.com", credentialsId: 'bindu29'

        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id

        stage "build"
        def app = docker.build "tomcat"

        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
