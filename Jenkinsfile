pipeline {
    agent any
        stages {
            stage('one') {
                steps {
                    echo 'Hi This is my first script'
                }
            }
            stage('two') {
                steps {
                    input('Do youb want to proceed?')
                }
            }
            stage('three') {
                when {
                    not {
                        branch "master"
                    }
                    
                }
                steps {
                    echo "Hello"
                }
            
            stage('four') {
                parallel {
                    stage("unit Test") {
                        steps {
                            echo "Running the Unit Test"
                        }
                    }
                    stage('Integrated Test') {
                        agent {
                            docker {
                                reuse node faulse
                                image 'ubuntu'
                            }
                        }
                        steps {
                            echo 'Running the integration test'
                        }
                    }
                }
            }    
            }
            
        }
}