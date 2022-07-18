pipeline {
    agent {
      node {label 'maven'}
    }
      parameters {
        choice(name: 'BROWSER_NAME', choices: ['chrome', 'firefox'], description: 'Pick the target browser in Selenoid')
        choice(name: 'BROWSER_VERSION', choices: ['103.0', '85.0', '78.0'], description: 'Pick the target browser version in Selenoid')
    }
      stages {
        
        stage ('Run tests'){
            steps {sh """
             mvn clean test
             """ 
                  } }
          stage ('Report'){
              steps {allure([
            includeProperties: false,
            properties: [],
            reportBuildPolicy: 'ALWAYS',
            results: [[path: 'target/allure-results']]
         ])
        }
          }
     }
}
