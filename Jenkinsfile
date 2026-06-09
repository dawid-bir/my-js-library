pipeline {
agent any

environment {
    NPM_TOKEN = credentials('npm-token')
}

tools {
    nodejs 'NodeJS' 
}

stages {
    stage('Build') {
        steps {
            sh 'npm install'
            sh 'npm run build'
        }
    }
    stage('Test') {
        steps {
            sh 'npm test'
        }
    }
    stage('Publish') {
        steps {
            sh 'echo "//registry.npmjs.org/:_authToken=${NPM_TOKEN}" > ~/.npmrc'
            sh 'npm publish --access public'
        }
    }
}
}