node {
       def app

       stage('Clone Repo') {
              checkout scm
       }

       stage('Build Image') {
               app = docker.build('caffeine2021/example-app')
       }

       stage('Test JS') {
              app.inside {
                  sh 'npm test'
              }
       }

       stage('Push Image') {
               docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                      app.push('latest')
                }
       }
}

