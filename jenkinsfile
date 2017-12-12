node {
  stage 'Run JMeter Test'
     step {
  //sh '/usr/local/bin/jmeter -n -t /usr/local/bin/Jenkins_demo1.jmx -l test.jtl'
  //echo "Running ${env.BUILD_ID} with ${env.JOB_NAME} on ${env.JENKINS_URL}"
  //sh '/usr/local/bin/jmeter -n -t /usr/local/bin/testplan.jmx -Jusers=250 -l /usr/local/bin/test/output.jtl -e -o /usr/local/bin/test/result'
      
      sh ' rm /usr/local/bin/test/*.jtl'  
      sh ' rm  -rf /usr/local/bin/test/result/* '
      sh '/usr/local/bin/jmeter -n -t /usr/local/bin/test/MVP1.0MaxLTV.v2.jmx  -l /usr/local/bin/test/output.jtl -e -o /usr/local/bin/test/result'
      }  
  stage 'Publish Jmeter report'
  
  step {

  
  //(its working) publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/usr/local/bin/test', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
    
    perfReport compareBuildPrevious: true, excludeResponseTime: true, modePerformancePerTestCase: true, modeThroughput: true, sourceDataFiles: '/usr/local/bin/test/*.jtl'
   //perfReport compareBuildPrevious: true, errorFailedThreshold: 10, errorUnstableThreshold: 0, excludeResponseTime: true, modePerformancePerTestCase: true, modeThroughput: true, sourceDataFiles:'/usr/local/bin/test/*.jtl'
  }
}
