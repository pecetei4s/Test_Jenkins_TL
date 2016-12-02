stage "Static Analysis Docker"

def response = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON',validResponseCodes: '100:501', httpMode: 'POST', requestBody: '{"repository": "mongo"}', url: ' http://10.23.100.245:8090/api/twistlock/reportHtml'
writeFile file: 'report.html', text: response.content
publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'report.html', reportName: 'Report TwistLock Static'])

stage "Dynamic Analysis Docker"
def response = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON',validResponseCodes: '100:501', httpMode: 'POST', requestBody: '{"container": "/reverent_colden"}', url: ' http://10.23.100.245:8090/api/twistlock/reportContainer'
writeFile file: 'reportContainer.html', text: response.content
publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'reportContainer.html', reportName: 'Report TwistLock Dynamic'])
