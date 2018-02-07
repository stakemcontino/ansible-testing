pipeline {
  agent any

  stages {
    stage ("Get Latest Code") {
      checkout scm
      sh 'git rev-parse HEAD > .git/commit-id'
    }
    stage ("Install Application Dependencies") {
      sh 'sudo pip show ansible'
      sh 'sudo pip show docker'
      sh 'sudo pip show molecule'
    }
    stage ("Executing Molecule lint") {
      sh 'molecule lint'
    }
    stage ("Executing Molecule create") {
      sh 'molecule create'
    }
    stage ("Executing Molecule converge") {
      sh 'molecule converge'
    }
    stage ("Executing Molecule idemotence") {
      sh 'molecule idempotence'
    }
    stage ("Executing Molecule verify") {
      sh 'molecule verify'
    }
    } catch(all) {
        currentBuild.result = "FAILURE"
        throw err
    }
}
