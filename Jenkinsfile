node ('VM-13') {
        stage('Checkout SCM') {
         echo 'Checkout progressing...'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'tfsid', url: 'https://tfs.symphonysummit.com/tfs/TestCollection/TestGit/_git/TestGit']]])
        }
         stage('NPM Setup') {
                echo 'downloading npm modules..'
                bat "npm install @angular-devkit/build-angular"
        }
        stage('Build') {
                echo 'Building..'
                bat "ng build"
        }
        stage('Unit Test') {
                echo 'Unit Testing..'
        }
        stage('Static Analysis') {
                echo 'Sonar Scanner Coverage'
        }
        stage('E2Etest') {
                echo 'end 2 end testing.....'
                bat "npm install protractor"
                bat "ng e2e"
        }
    }