pipeline {
    agent any
    tools {
        maven 'MAVEN'
        jdk 'JAVA'
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
