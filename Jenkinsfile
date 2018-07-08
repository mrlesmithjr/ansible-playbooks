#!/usr/bin/env groovy

node {
    deleteDir()

    try {
      stage ('Clone') {
        checkout scm
      }
      stage ('Bootstrap') {
        sshagent (credentials: ['vagrant']) {
          ansiblePlaybook(
            inventory: '${WORKSPACE}/inventory',
            playbook: '${WORKSPACE}/bootstrap/playbook.yml',
            colorized: true
            )
        }
      }
    }
    catch (err) {
      currentBuild.result = "Failed"
      throw err
    }
}
