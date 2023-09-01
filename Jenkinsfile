node{

   def tomcatWeb = 'C:\\Users\\iliyas\\Downloads\\apache-tomcat-10.1.13-windows-x64\\apache-tomcat-10.1.13\\webapps'
   def tomcatBin = 'C:\\Users\\iliyas\\Downloads\\apache-tomcat-10.1.13-windows-x64\\apache-tomcat-10.1.13\\bin'
   
   // 'D:\\Auto_deployment\\apache-tomcat-9.0.30\\apache-tomcat-9.0.30\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/sivajavatechie/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\pipeline_tomcat.war \"${tomcatWeb}\\pipeline_tomcat.war\"
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
