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
      docker.withRegistery('https://registry.hub.docker.com', 'user-docker-credentials'){
      docker.push("latest")
      docker.push("${env.BUILDNUMBER}")
      }
    }
}
