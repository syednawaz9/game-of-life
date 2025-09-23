pipeline {
    agent { label 'NODE1_172.31.30.132' }
    options {
        timeout(time: 30, unit: 'HOURS') 
    }
    triggers {
        { pollSCM('* * * * *') }
    }
    tools {
        jdk 'JDK_8'
    }

    stages {
        stage ('vcs') {
            steps{ 
                git url: 'https://github.com/muthyalasaikiran/game-of-life.git',
                    branch: 'master'
            }
        }
        stage  ('package') {
            steps {
                sh script: 'mvn package'
            }
        }
        
    }
}   