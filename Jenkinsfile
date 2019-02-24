//@Library("example")_
//startPipeline(team_url: env.TEAMURL)

def isOnlyVersionBump() {
    def fullFileName = ""
    for (changeSet in currentBuild.changeSets) {
        for (item in changeSet.items) {
            for (file in item.affectedFiles) {
                if ( 1 < item.affectedFiles.size() ) {
                    return false
                }
                fullFileName = file.path
                if ( "version.sbt" == fullFileName.substring(fullFileName.lastIndexOf("/")+1) ) {
                    return true
                }
            }
        }
    }
    return false
}

def getChangeFile() {
    println currentBuild.changeSets.size()
}

pipeline {
    agent any

     stages {
         stage('Clone repository and build tests') {
             steps {
                 sh 'ls -la'
                 getChangeFile()
             }
         }
     }
}

