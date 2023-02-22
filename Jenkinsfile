pipeline {
    agent any
}
stage('Deploy') {
  agent any
  steps {
    sh 'mv target/my-app-0.0.1-SNAPSHOT.jar my-app.jar'
    sshPublisher(
      continueOnError: false, 
      failOnError: true,
      publishers: [
        sshPublisherDesc(
          configName: "my-ssh-connection",
          transfers: [sshTransfer(sourceFiles: 'my-app.jar')],
          verbose: true
        )
      ]
    )
  }
}