def call(String Project, String ImageTag, String DockerHubUser) {

    withCredentials([
        usernamePassword(
            credentialsId: 'dockerhubcred',
            usernameVariable: 'DOCKERHUB_USER',
            passwordVariable: 'DOCKERHUB_PASS'
        )
    ]) {

        sh """
            echo "\$DOCKERHUB_PASS" | docker login -u "\$DOCKERHUB_USER" --password-stdin
            docker push ${DockerHubUser}/${Project}:${ImageTag}
            docker logout
        """
    }
}
