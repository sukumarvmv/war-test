node {
      
      stage ('checkout') {
          
           git credentialsId: 'github', url: 'https://github.com/sukumarvmv/war-test.git'
          
      }
    
      stage ('build') {
          
          echo 'build is in progress'
       
          def mavenHome = tool name: 'maven3',type: 'maven'
          def mavenCMD =  "${mavenHome}/bin/mvn"
          sh "${mavenCMD} clean package" 

          
          
      }
      
      stage ('deploy') {
          echo 'deploy is in progress'
          
          deploy adapters: [tomcat9(credentialsId: 'tomcatcred', path: '', url: 'http://35.238.1.38:8080')], contextPath: 'wartetdeploy', war: '**/*.war'
      }
      
    
}
