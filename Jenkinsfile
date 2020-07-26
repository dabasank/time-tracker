pipeline {
    agent any
    tools {
        Maven 'Maven 3.6.3'
        Java 'jdk 1.8.0'
    }
        stages {
            stage('FETCH') {
                steps {
                    echo "FETCHING CODE FROM GIT REPOSITORY"
                    git 'https://github.com/dabasank/time-tracker.git'
                }
            }
            stage('INITIALIZE'){
                steps {
                    sh '''
                        echo "PATH=${PATH}"
                        echo "MAVEN_HOME = ${MAVEN_HOME}"
                    '''
                }
            }
            stage('BUILD') {
                steps {
                    echo "BUILDING THE SOURCE CODE"
                    sh 'mvn install'
                }
            }
    }
}
