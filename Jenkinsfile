pipeline {
  agent any
  stages {
    stage('Changed Files Check') {
      steps {
        echo 'This stage is to check which files were changed of the microservice'
        writeFile(file: 'CommitStat.txt', text: 'a')
        sh '''git show --stat > CommitStat.txt

cat CommitStat.txt'''
        writeFile(file: 'grepping.txt', text: 'b')
        writeFile(file: 'unicity.txt', text: 'c')
        writeFile(file: 'FinalResult.txt', text: 'd')
        sh '''set +e
grep -E Code\\|Ship\\_Package CommitStat.txt > grepping.txt
cat grepping.txt
cat grepping.txt | cut -d/ -f1 grepping.txt > unicity.txt
'''
        sh '''uniq unicity.txt > FinalResult.txt

echo "le/(s/) dossier/(s/) impact/�s par un changement sont :
 
cat FinalResult.txt'''
      }
    }

    stage('Running Code') {
      steps {
        echo 'The folder code should always be on the run '
      }
    }

    stage('Check&Run') {
      steps {
        echo 'this step should check if ship_package was changed and then run it'
      }
    }

  }
}