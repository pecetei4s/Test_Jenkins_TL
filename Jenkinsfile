node(){
def response = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody: '{"repository": "elastic"}', url: ' http://10.0.2.15:8090/api/twistlock/reportHtml'
writeFile file: 'report.html', text: response.content
publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, keepAll: true, reportDir: '', reportFiles: 'report.html', reportName: 'Report TwistLock'])
}
