pipeline {
    agent {label 'GOL'}
    options {
        timeout(time: 30, unit: 'HOURS') 
    }
    triggers {
        pollSCM('* * * * *')
    }
    tools {
        jdk 'JDK_8'
        maven 'maven 3.9.12'
    }
    parameters { 
        choice(name: 'GOALS', 
        choices: ['mvn clean install','mvn jetty:run'],  
        description: 'Select maven goals to execute') 
        }

    stages {
        stage ('vcs') {
            steps{ 
                git url: 'https://github.com/syednawaz9/game-of-life.git',
                    branch: 'master'
            }
        }
        stage  ('GOALS') {
            steps {
                echo "maven_goals: ${params.GOALS}"
            }
        }
        
    }
}   