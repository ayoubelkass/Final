pipeline {
  agent any
  stages {
    stage('Changed Files Check') {
      steps {
        echo 'This stage is to check which files were changed of the microservice'
        writeFile(file: 'CommitStat.txt', text: 'a')
        writeFile(file: 'grepping.txt', text: 'b')
        writeFile(file: 'unicity.txt', text: 'c')
        writeFile(file: 'FinalResult.txt', text: 'd')
        sh '''git show --stat > CommitStat.txt

cat CommitStat.txt'''
        sh '''set +e

grep -E Code\\|Ship\\_Package CommitStat.txt > CommitStat.txt

cat CommitStat.txt

cut -d/ -f1 CommitStat.txt > unicity.txt
'''
        sh '''uniq unicity.txt > CommitStat.txt

echo "le dossier ou les dossiers impactes par un changement sont :"
 
cat CommitStat.txt'''
      }
    }

    stage('Running Code') {
      steps {
        echo 'The folder code should always be on the run '
        sh '''cd Code 
ls'''
      }
    }

    stage('Check&Run') {
      environment {
        variable = 'b'
      }
      steps {
        echo 'this step should check if ship_package was changed and then run it'
        readFile 'CommitStat.txt'
        script {
          variable=readFile('CommitStat.txt').trim()
        }

        echo "dossier :  ${variable}"
      }
    }

  }
}