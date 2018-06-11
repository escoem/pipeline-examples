
def content = readTrusted('package.json')
echo content

def json = readJSON(text: content)
def version = json.version
echo version
content = "9.11.1"


def label = "mypod-${UUID.randomUUID().toString()}"
podTemplate(label: label, containers: [
    containerTemplate(name: 'node',    image: "node:$version", ttyEnabled: true, command: 'cat'),
    containerTemplate(name: 'appnode', image: 'node:8.11.2', ttyEnabled: true, command: 'cat')
  ]) {
  
  node(label) {
    checkout scm
    
    container ('node') {
      sh 'ls -la'
      sh 'node --version'
      sh 'touch miratuquebien'
    }
    
    container ('appnode') {
      sh 'ls -la'
      sh 'node --version'
    }
  }
  
}
