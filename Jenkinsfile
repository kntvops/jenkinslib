#!groovy

@Library('jenkinslib') _  // jenkinslib 库引用 

def tools = new org.devops.tools() // jenkinslib  工具定义

String workspace = "/opt/jenkins/workspace"

// Pipeline
pipeline{
    agent { node { label "build"	//指定运行节点的标签或者名称
			customWorkspace "${workspace}" 	// 指定运行工作目录(可选)
			}
	}

	options {
		timestamps() // 日志会有时间
		skipDefaultCheckout()	//删除隐式checkout scm 语句
		disableConcurrentBuilds() // 禁止并行
		timeout(time: 1, unit: 'HOURS')	//流水线超时设置1h
	}
    

    //流水线的阶段
    stages{

        //阶段1 获取代码
        stage("CheckOut"){
            steps{
                script{
                    println("获取代码")

					tools.PrintMes("this is my jenkinslib") // jenkinslib 调用方法
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    println("运行构建")
                }
            }
        }
    }
    post {
        always{
            script{
                println("流水线结束后，经常做的事情")
            }
        }
        
        success{
            script{
                println("流水线成功后，要做的事情")
            }
        
        }
        failure{
            script{
                println("流水线失败后，要做的事情")
            }
        }
        
        aborted{
            script{
                println("流水线取消后，要做的事情")
            }
        
        }
    }
}
