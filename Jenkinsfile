pipeline {
    agent any
    options {
        timeout(time: 30, unit: 'HOURS') 
    }
    triggers {
        { pollSCM('* * * * *') }
    }
    tools {
        jdk 'JDK_8'
    }
    tools{
        maven 'maven 3.9.12'
    }
    parameters { 
        choice(name: 'GOALS', 
        choices: ['mvn clean install',],  
        description: 'Select maven goals to execute') }

    stages {
        stage ('Git clone') {
            steps{ 
                git url: 'https://github.com/syednawaz9/game-of-life.git,
                    branch: 'master'
            }
        }
        stage('MAVEN_GOALS') {
            steps {
                echo "maven_goals: ${params.GOALS}"
            }
        }
        
    }
}   