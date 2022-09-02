pipeline {
    agent any
    stages {
        stage('run') {
            steps {
                echo 'Clarusway_Way to Reinvent Yourself....'
                sh 'python --version'
                sh 'python pipeline.py'
            }
        }
       
        stage("Display changeset") {
            steps {
                script {
                def changeLogSets = currentBuild.changeSets
                for (int i = 0; i < changeLogSets.size(); i++) {
                def entries = changeLogSets[i].items
                for (int j = 0; j < entries.length; j++) {
                    def entry = entries[j]
                    def files = new ArrayList(entry.affectedFiles)
                    for (int k = 0; k < files.size(); k++) {
                        def file = files[k]
                        print file.path 
                    if (filePath.contains("current/common")) {
                                                // Set UPDATE_PATH to empty to build all jobs
                        updatePath = ""
                        break;
                    }
                    elif (filePath.contains("current/projects")) {
                        updatePath = updatePath + ":jjb/jobs/${filePath}"
                    }
                    elif (filePath.contains("current/auth")) {
                         def splitPath = filePath.split("auth")
                         updatePath = updatePath + ":jjb/jobs/current/projects${splitPath[1]}"
                    }
                   }
                 }
               }
             }
           }
        }
     }
}
