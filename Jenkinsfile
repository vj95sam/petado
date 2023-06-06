pipeline{
 agent any
 stages{
     stage('build'){
         steps{
             git 'https://github.com/kalpanakutty/Devops.git'
             sh "./mvnw compile"
             echo 'Building the project with maven compile'
         }
     }
     stage('Test'){
         steps{
             sh "./mvnw test"
             echo 'Testing the project with maven test'    
                  }

     }
     stage(package){
         steps{
             sh "./mvnw package"
             echo 'Packing the project with maven package'
         }
     }
 stage(containerize){
         steps{
             sh "docker build -t pet-clinic-image ."
             echo 'containerizing the app with docker'
         }
 }
 stage(Deploy){
         steps{
             sh "docker run -d -p 9090:9090 pet-clinic-image"
             echo 'Deploy the app with docker'
         }
 }
 }
}
