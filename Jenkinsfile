@Library('pipeline-library-demo')_

def my_ref_method(String name = 'human') {
  echo "Hello, ${name}."
  echo "Hello, ${name}."
} 
node('maven-label') {
   def mvnHome
   stage('Preparation') { 
      
     git branch: "$branch_name", url: 'https://github.com/IP-RandD/ghub.git'
                 
      mvnHome = tool 'maven-3.6.2'
   }
   stage('Build') {
      
      withEnv(["MVN_HOME=$mvnHome"]) {
         if (isUnix()) {
            sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
         } else {
            bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package/)
         }
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
   stage('my-ref-meth'){
     my_ref_method "Intellipath"
   }
  stage('my-shared-lib'){
     sayHello1 "devops"
   }
      
}
