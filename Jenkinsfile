pipeline {
    agent any

    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'اختار الفرع')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'تشغل مرحلة الـ Deploy؟')
        choice(name: 'ENV', choices: ['dev', 'test', 'prod'], description: 'اختار البيئة')
    }

    stages {
        stage('Checkout') {
            steps {
                echo "جاري تحميل الكود من الفرع: ${params.BRANCH}"
                git branch: params.BRANCH, url: 'https://github.com/OmarEltabakh123/jenkins-parameterized-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo "بيتم البناء للبيئة: ${params.ENV}"
            }
        }

        stage('Deploy') {
            when {
                expression { return params.DEPLOY }
            }
            steps {
                echo "بيتم النشر في بيئة ${params.ENV}"
            }
        }
    }
}

