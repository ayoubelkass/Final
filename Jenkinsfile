pipeline {
  agent any
  stages {
    stage('Changed Files Check') {
      steps {
        echo 'This stage is to check which files were changed of the microservice'
        writeFile(file: 'FinalResult.txt', text: 'd')
        sh '''git show --stat > FinalResult.txt

cat FinalResult.txt'''
        sh '''set +e

grep -E Code\\|Ship\\_Package FinalResult.txt > FinalResult.txt

cat FinalResult.txt | cut -d/ -f1 FinalResult.txt > FinalResult.txt
'''
        sh '''uniq FinalResult.txt > FinalResult.txt

echo "le dossier ou les dossiers impactes par un changement sont :"
 
cat FinalResult.txt'''
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
        big = 'a'
        variable = 'b'
      }
      steps {
        echo 'this step should check if ship_package was changed and then run it'
        echo "my name is ${big}youb"
        readFile 'FinalResult.txt'
        script {
          variable=readFile('FinalResult.txt').trim()
        }

        echo "dossier :  ${variable}"
      }
    }

  }
}