pipeline {
    agent any
    stages {
        stage('one') {
                steps {
                    echo 'KONICHIWA !'    
                }
            } 
        stage('two') {
                steps {
                    echo 'Now jenkins stage 2'
                }
            }

        stage('three') {
                when {
                    not {
                            branch "master"
                        }
                }
                steps {
                    echo "stage 3"
                    }
            }

        stage('four') {
                parallel {
                    stage ('unit test') {
                            steps {
                                echo "Running unit test...."    
                            }
                        } 
                    stage ('Integration test') {
                            agent {
                                docker {
                                    reuseNode true
                                    image 'ubuntu'
                                }    
                            }
                            steps {
                                echo "Running the integration test..."    
                            }
                        
                        }
                }
            }
    
    }
}
