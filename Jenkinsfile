pipeline {
    agent {
		node {
			label "master"
			customWorkspace "D:\\Git Traning\\Jenkins\\workspaces\\asp.net-example-scmpipeline"
		}
	}
    stages {
        stage('Build') {
            steps {
                		bat "D:\\Git Traning\\Tools\\nuget\\nuget.exe restore"
				bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Enterprise\\MSBuild\\15.0\\Bin\\amd64\\MSBuild.exe" Bank\\Bank.csproj'
				bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Enterprise\\MSBuild\\15.0\\Bin\\amd64\\MSBuild.exe" BankTest\\BankTest.csproj'
            }
        }
        stage('Test') {
            steps {
				bat "D:\\Git Traning\\Tools\\mstest\\MSTest.exe /resultsfile:BankTestFirstRun.trx /noisolation /testcontainer:%WORKSPACE%\\BankTest\\bin\\Debug\\BankTest.dll"
				bat '"D:\\Git Traning\\Tools\\opencover\\tools\\OpenCover.Console.exe" -register:administrator -target:"C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\Common7\\IDE\\MSTest.exe" -targetargs:"/testcontainer:\\"%WORKSPACE%\\BankTest\\bin\\Debug\\BankTest.dll\\" /resultsfile:\\"%WORKSPACE%\\BankTestResults.trx\\"" -mergebyhash -skipautoprops -output:"%WORKSPACE%\\Coverage.xml" -filter:"+[Bank*]* -[BankTest]*"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Hello world!' 
            }
        }
    }
}
