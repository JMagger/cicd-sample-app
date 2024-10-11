properties([pipelineTriggers([githubPush()])])

node {
        git url: 'https://github.com/JMagger/cicd-sample-app',branch: 'main'
        stage ('Compile Stage') {

            echo "compiling"
            echo "compilation completed"
        }
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning'
            sh 'docker rm samplerunning'
        }
    }
    stage('Build') {
        build 'BuildSampleApp'
    }
    stage('Results') {
        build 'TestSampleApp'
    }
}