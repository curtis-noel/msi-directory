node {
        stage('build') {
            checkout scm
        }

        stage('dockerization') {

          def app = docker.build("wolf685cln/msi-directory-${environment}")
          docker.withRegistry('https://registry.hub.docker.com','docker-login') {
              app.push 'latest'
          }
        }

        stage('cleanup') {
          step([$class: 'WsCleanup'])
        }
}
