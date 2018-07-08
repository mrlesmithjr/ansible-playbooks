#!/usr/bin/env groovy

node {
    def ansibleCredsId = "a490c6ab-bf59-4e2a-be13-a3ad8678344f"
    def ansibleForks = 5

    deleteDir()

    try {
      stage ('Clone') {
        checkout scm
      }
      stage ('Bootstrap') {
        ansiColor('xterm') {
          ansiblePlaybook(
            inventory: '${WORKSPACE}/inventory',
            playbook: '${WORKSPACE}/bootstrap/playbook.yml',
            colorized: true,
            credentialsId: '${ansibleCredsId}'
            )
        }
      }
      stage ('Base') {
        ansiColor('xterm') {
          ansiblePlaybook(
            inventory: '${WORKSPACE}/inventory',
            playbook: '${WORKSPACE}/base/playbook.yml',
            colorized: true,
            credentialsId: '${ansibleCredsId}'
            )
        }
      }
    }
    catch (err) {
      currentBuild.result = "Failed"
      throw err
    }
}
