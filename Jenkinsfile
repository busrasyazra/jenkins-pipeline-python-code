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
                        print files
                        print file.path 
                        tfValidatePaths = []
                        //updatePath = "jjb/jobs/current/common"
                        /*if (file.path.contains("current/common")) {
                            print updatePath
                        }
                        else if (file.path.contains("current/projects")) {
                            updatePath = updatePath + ":jjb/jobs/${file.path}"
                            print updatePath
                        }    
                        else if (file.path.contains("current/auth")) {
                            updatePath = updatePath + ":jjb/jobs/${file.path}"
                            print updatePath
                        }*/
                        if (file.path.startsWith("src/com/arcgis")) {
                            //def splitPath = file.path.split("\n")
                            //updatePath = updatePath + ":jjb/jobs/current/projects${splitPath[1]}"
                            //splitPath //updatePath
                            tfValidatePaths = tfValidatePaths + file.path
                            print tfValidatePaths
                        }
                   }
                 }
               }
             }
           }
        }
     }
}
