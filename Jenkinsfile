node(){
def response = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody: '{"repository": "pecete"}', url: ' http://10.0.2.15:8090/api/twistlock/reportHtml'
def f = new File("/home/tmp/report.html")
f.write(response, "UTF-8")
publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: /home/tmp/, reportFiles: 'report.html', reportName: 'Report TwistLock'])
}
