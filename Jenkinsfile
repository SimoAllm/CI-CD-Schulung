pipeline {
    agent any

    options {
        timeout(time: 1, unit: 'MINUTES')
    }

    environment {
        var1 = 'Hugo'
        var2 = '42'
    }

    stages {
        stage('stage1') {
            steps {
                echo "Var1 hat den Wert ${env.var1}"
            }
        }

        stage('Schreibe Datei') {
            steps {
                writeFile file: 'meineDatei.txt', text: 'Hallo, Jenkins!'
                stash includes: 'meineDatei.txt', name: 'meineDatei'
            }
        }

        stage('Lese Datei') {
            steps {
                unstash 'meineDatei'
                echo readFile('meineDatei.txt')
            }
        }
    }
}
