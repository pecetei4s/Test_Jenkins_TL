node(){


stage "Build Docker"  
    httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON',validResponseCodes: '100:501',consoleLogResponseBody: true, httpMode: 'POST', url: 'http://10.23.100.245:2375/images/create?fromImage=busybox&tag=latest'

stage "Run Container"  
  httpRequest acceptType: 'APPLICATION_JSON', requestBody: '{"Image": "localhost:5000/armadillo-standalone-alpine:2.2.2"}',contentType: 'APPLICATION_JSON',validResponseCodes: '100:501',consoleLogResponseBody: true, httpMode: 'POST', url: 'http://10.23.100.245:2375/containers/create?name=Armadillo1'
  httpRequest acceptType: 'APPLICATION_JSON',contentType: 'APPLICATION_JSON',validResponseCodes: '100:501',consoleLogResponseBody: true, httpMode: 'POST', url: 'http://10.23.100.245:2375/containers/Armadillo1/start?name=Armadillo1'

stage "Static Analysis Docker"
  def response = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON',validResponseCodes: '100:501', httpMode: 'POST', requestBody: '{"repository": "armadillo-standalone-alpine:2.2.2"}', url: ' http://10.23.100.245:8090/api/twistlock/reportHtml'
  writeFile file: 'report.html', text: response.content

stage "Dynamic Analysis Docker"
  def response1 = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON',validResponseCodes: '100:501', httpMode: 'POST', requestBody: '{"container": "/Armadillo1"}', url: ' http://10.23.100.245:8090/api/twistlock/reportContainer'
  writeFile file: 'reportContainer.html', text: response1.content

stage "Stop Container"
      httpRequest acceptType: 'APPLICATION_JSON',contentType: 'APPLICATION_JSON',validResponseCodes: '100:501',consoleLogResponseBody: true, httpMode: 'POST', url: 'http://10.23.100.245:2375/containers/Armadillo1/stop'
      httpRequest acceptType: 'APPLICATION_JSON',contentType: 'APPLICATION_JSON',validResponseCodes: '100:501',consoleLogResponseBody: true, httpMode: 'DELETE', url: 'http://10.23.100.245:2375/containers/Armadillo1'
  
stage "Report Twistlock"
  publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'report.html', reportName: 'Report TwistLock Static'])
  publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'reportContainer.html', reportName: 'Report TwistLock Dynamic'])

}
 
