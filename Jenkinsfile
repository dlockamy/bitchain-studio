pipeline {
  agent any

  environment {
    NEXUS_URL  = 'https://nexus.softsurve.com'
    REGISTRY   = 'nexus.softsurve.com'
    IMAGE_NAME = 'bitchain-studio'
  }

  stages {

    stage('Pre-flight') {
      steps {
        script {
          def msg = sh(script: 'git log -1 --pretty=%B', returnStdout: true).trim()
          if (msg.contains('[skip ci]')) {
            currentBuild.result = 'NOT_BUILT'
            error('Commit contains [skip ci] — aborting.')
          }
        }
      }
    }

    // Placeholder build stage — expand when app framework is chosen
    stage('Build') {
      steps {
        echo 'bitchain-studio: no build target yet. Add build steps when framework is selected.'
        sh 'ls -la'
      }
    }

    // Docker build and push when a Dockerfile exists
    stage('Docker') {
      when {
        expression { fileExists('Dockerfile') }
      }
      steps {
        script {
          def shortSha = sh(script: 'git rev-parse --short HEAD', returnStdout: true).trim()
          def imageTag  = "${env.REGISTRY}/${env.IMAGE_NAME}:${shortSha}"
          def latestTag = "${env.REGISTRY}/${env.IMAGE_NAME}:latest"
          env.IMAGE_TAG = imageTag

          withCredentials([usernamePassword(
            credentialsId: 'nexus-credentials',
            usernameVariable: 'NEXUS_USER',
            passwordVariable: 'NEXUS_PASS'
          )]) {
            sh """
              echo "${NEXUS_PASS}" | docker login ${env.REGISTRY} \
                -u "${NEXUS_USER}" --password-stdin
              docker build -t "${imageTag}" -t "${latestTag}" .
              docker push "${imageTag}"
              docker push "${latestTag}"
              docker logout ${env.REGISTRY}
            """
          }
        }
      }
    }

  }

  post {
    always { cleanWs() }
  }
}
