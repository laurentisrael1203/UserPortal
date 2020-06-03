node{

   
   def tomcatWeb = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps'
   def tomcatBin = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin'
   def tomcatStatus = ''
   
   stage('SCM Checkout'){
   snDevOpsStep()
      git 'https://github.com/laurentisrael1203/UserPortal.git'
     }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
   snDevOpsStep()
      def mvnHome =  tool name: 'Maven 3.6.3', type: 'maven'   
      bat "mvn package"
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
   snDevOpsStep()
      snDevOpsChange()
     bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
     /* stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "cd ${tomcatBin}"
         bat "startup.bat"
         sleep(time:100,unit:"SECONDS")
   }*/
}

