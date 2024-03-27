pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Testing..'
                deleteDir()
                // Get some code from a GitHub repository
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ngahn15/Demo.git']])
                
                bat '''
                    set nameJob=%cd%
                    cd ..
                    cd Katalon_Studio_Engine_Windows
                    katalonc -noSplash -runMode=console -projectPath="%nameJob%\\POC_Demo.prj" -retry=0 -testSuitePath="Test Suites/AllTest" -browserType="Chrome" -executionProfile="default" -apiKey="34873e07-4272-478f-93be-6e352853925f" --config -proxy.auth.option=NO_PROXY -proxy.system.option=NO_PROXY -proxy.system.applyToDesiredCapabilities=true -webui.autoUpdateDrivers=true
                ''' 

            }

            
        }
    }
}
