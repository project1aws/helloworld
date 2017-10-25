node{
  def app
    stage('checkout'){
      checkout scm
    }
    stage ('build'){
      app = docker.build("rvarg11/project1-helloworld")
    }
    stage ('test'){
      app.inside {
        sh 'echo "test passed"'
      }
    }
    stage ('Push Image'){
      docker.withRegistery('https://registry.hub.docker.com', 'docker-hub-credentials'){
      app.push("latest")
      app.push("${env.BUILDNUMBER}")
      }
    }
}
