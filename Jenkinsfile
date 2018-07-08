#!/usr/bin/env groovy

node {
    deleteDir()

    try {
      stage ('Clone') {
        checkout scm
      }
      stage ('Bootstrap') {
        ansiblePlaybook(
          inventory: '${WORKSPACE}/inventory',
          playbook: '${WORKSPACE}/bootstrap/playbook.yml',
          colorized: true,
          credentialsId: 'a490c6ab-bf59-4e2a-be13-a3ad8678344f'
          )
      }
    }
    catch (err) {
      currentBuild.result = "Failed"
      throw err
    }
}
