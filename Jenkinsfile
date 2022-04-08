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
        sh '''set +e
rep -E Code\\|Ship\\/Package CommitStat.txt > grepping.txt
 cat grepping.txt | cut -d/ -f1 grepping.txt
'''
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