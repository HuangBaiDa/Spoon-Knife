pipeline {
    // 使用自定义 Docker 镜像并挂载卷来运行流水线
    agent {
        docker {
            // 指定自定义 Docker 镜像
            image 'maven:3.9.0'
            // 挂载卷
            args '-v /root/.m2:/root/.m2'
        }
    }

    stages {
        stage('Build') {
            steps {
                // 在这里定义构建步骤
                // 例如：使用 Docker 构建和运行应用程序
                // 在这里添加构建步骤
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
                    steps {
                        sh 'mvn test'
                    }
                    post {
                        always {
                            junit 'target/surefire-reports/*.xml'
                        }
                    }
        }
        // 添加其他流水线阶段和步骤
        stage('Deliver') {
                steps {
                    sh './jenkins/scripts/deliver.sh'
                }
        }
    }
}
