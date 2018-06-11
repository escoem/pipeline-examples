
def content = readTrusted('package.json')
echo content

content = "9.11.1"


def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, containers: [
    containerTemplate(name: 'node',    image: "node:$content", ttyEnabled: true, command: 'cat'),
    containerTemplate(name: 'appnode', image: 'node:8.11.2', ttyEnabled: true, command: 'cat')
  ]) {
  
  node(label) {
    checkout scm
    
    container ('node') {
      sh 'ls -la'
      sh 'node --version'
      sh 'touch miratuquebien'
    }
    
    container ('nodeapp') {
      sh 'ls -la'
      sh 'node --version'
    }
  }
  
}
