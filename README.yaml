trigger:
- main

pool:
  vmImage: 'ubuntu-latest'


steps:
- script: |
    echo "check bsdtar is present"
    if ! command -v bsdtar $> /dev/null
    then 
    echo "Its not present,hence installing unzip"
    sudo apt-get update
    sudo apt-get install -y unzip
    else
    echo "bsdtar is there"
    fi

  displayName: 'checking pre req'
  
- script: |
    echo "Installing sonarscanner"
    sonar_scanner_version="6.1.0.4477"
    sonar_scanner_zip="6.1.0.4477.zip"
    sonar_scanner_url="https://github.com/SonarSource/sonar-scanner-cli/archive/refs/tags/6.1.0.4477.zip"
    wget $sonar_scanner_url -O $sonar_scanner_zip
    
    export PATH=$PATH:$HOME/sonar-scanner/sonar-scanner-cli-$sonar_scanner_version/bin
    sonar-scanner --version
    
    echo "Starting SonarCloud Analysis"
    sonar-scanner -X \
      -Dsonar.projectKey="xxyy" \
      -Dsonar.organization="xx" \
      -Dsonar.sources=. \
      -Dsonar.host.url="https://sonarcloud.io" \
      -Dsonar.login=$(SONAR_TOKEN)
  displayName: 'Run SonarCloud Analysis with Bash'

- task: SonarCloudPublish@2
  inputs:
    pollingTimeoutSec: '300'
