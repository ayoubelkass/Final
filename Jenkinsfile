pipeline {
  agent any
  stages {
    stage('Changed Files Check') {
      steps {
        echo 'This stage is to check which files were changed of the microservice'
        sh '''git show --stat > CommitStat.txt
 grep -E Code\\|Ship\\_Package CommitStat.txt > grepping.txt
 cat grepping.txt | cut -d/ -f1 grepping.txt > unicity.txt
 uniq unicity.txt > FinalResult.txt
 var=$(cat FinalResult.txt)
 echo "le(s) dossier(s) impactés par un changement sont : 
 $var "  '''
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