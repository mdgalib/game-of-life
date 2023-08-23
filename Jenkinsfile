pipeline {
    agent any 
    triggers { pollSCM('*/2 * * * *') }
    stages {
        stage('cloning gol url') {             
            steps {
                git 'https://github.com/mdgalib/game-of-life.git'
            }
        }
        stage('Building code and creating artifact') {
            tools{
                jdk 'jdk8'
            }   
            steps {
                sh 'mvn package'
            }
        }   
        stage('arching artifacts'){
            steps{
                archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false

            }
        }    
    }
}