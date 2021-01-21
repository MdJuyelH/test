pipeline {
  agent any
  stages {
    stage('tool') {
      steps {
        tool(name: 'JDK', type: 'Oracle Java 8')
      }
    }

    stage('npm') {
      steps {
        nodejs 'NodeJS 12.14.1'
      }
    }

    stage('command') {
      steps {
        sh '''npm rebuild node-sass
npm install
npm run build
npm run build-storybook '''
      }
    }

    stage('s3') {
      steps {
        s3Upload 'test'
      }
    }

  }
}