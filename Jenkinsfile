pipeline {
  agent any
  stages {
    stage('Changed Files Check') {
      steps {
        writeFile(file: 'CommitStat.txt', text: 'a')
        writeFile(file: 'grepping.txt', text: 'b')
        writeFile(file: 'unicity.txt', text: 'c')
        writeFile(file: 'FinalResult.txt', text: 'd')
        sh '''git show --stat > CommitStat.txt
              cat CommitStat.txt'''
        sh '''set +e
              grep -E Code\\|Ship\\_Package CommitStat.txt > grepping.txt
              cut -d/ -f1 grepping.txt > unicity.txt'''
        sh '''uniq unicity.txt > FinalResult.txt
              echo "le(s) dossier(s) impacte(s) par un changement sont :"
              cat FinalResult.txt'''
      }
    }

    stage('Running Code') {
      steps {
        sh '''cd Code 
              ls'''
      }
    }

    stage('Push Docker image to Docker registry') {
      
      steps {
        echo 'hello there ..!'
      }
    }

    stage('Check&Run') {
      when {
        expression {
          return readFile('FinalResult.txt').contains('Ship')
        }

      }
      environment {
        variable = 'The running of ship/package has happened'
      }
      steps {
        echo "${variable}"
      }
    }

  }
}