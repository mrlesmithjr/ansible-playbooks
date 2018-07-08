#!/usr/bin/env groovy

node {
    deleteDir()

    try {
      stage ('Clone') {
        checkout scm
      }
      stage ('Bootstrap') {
        ansible-playbook -i inventory/ bootstrap/playbook.yml
      }
    }
    catch (err) {
      currentBuild.result = "Failed"
      throw err
    }
}
