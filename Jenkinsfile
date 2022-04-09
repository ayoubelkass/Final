pipeline {
  agent any
  stages {
    stage('Changed Files Check') {
      steps {
        echo 'This stage is to check which files were changed of the microservice'
        writeFile(file: 'FinalResult.txt', text: 'd')
        writeFile(file: 'arc.txt', text: 'a')
        sh '''git show --stat > FinalResult.txt

cat FinalResult.txt'''
        sh '''set +e

grep -E Code\\|Ship\\_Package FinalResult.txt > FinalResult.txt

cat FinalResult.txt | cut -d/ -f1 FinalResult.txt > FinalResult.txt
'''
        sh '''uniq FinalResult.txt > arc.txt

echo "le dossier ou les dossiers impactes par un changement sont :"
 
cat arc.txt'''
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
        readFile 'arc.txt'
        script {
          variable=readFile('arc.txt').trim()
        }

        echo "dossiers :  ${variable}"
      }
    }

  }
}