#!/usr/bin/env groovy

node {
    deleteDir()

    try {
      stage ('Clone') {
        checkout scm
      }
    }
    catch (err) {
      currentBuild.result = "Failed"
      throw err
    }
}
