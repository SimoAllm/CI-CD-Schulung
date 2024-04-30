pipeline {
    agent any

    options {
        timeout(time: 1, unit: 'MINUTES')
    }

    environment {
        var1 = 'Hugo'
        var2 = '42'
        varFileContents = ''
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

        stage('Schreibe dynamisch berechneten Dateiinhalt') {
            steps {
                script {
                    def text = ''

                    for (int i = 0; i < 10; i++) {
                        text += 'Hallo, Jenkins! '
                    }

                    writeFile file: 'meineZweiteDatei.txt', text: text
                    stash includes: 'meineZweiteDatei.txt', name: 'meineZweiteDatei'
                }
            }
        }

        stage('Lese Datei mit dynamischem Inhalt'){
            steps {
                script {
                    unstash 'meineZweiteDatei'
                    env.varFileContents = readFile('meineZweiteDatei.txt')
                    echo "Inhalt der Datei mit dynamischem Inhalt: ${env.varFileContents}"
                }
            }
        }
    }
}
