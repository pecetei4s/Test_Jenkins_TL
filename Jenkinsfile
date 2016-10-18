node(){
def response = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody: '{"repository": "pecete"}', url: ' http://10.0.2.15:8090/api/twistlock/reportHtml'
publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: response, reportFiles: 'Report_TwistLock.html', reportName: 'Report TwistLock'])
}
