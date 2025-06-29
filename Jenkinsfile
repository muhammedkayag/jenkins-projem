// Declarative Pipeline syntax'ı
pipeline {
    agent any // Bu pipeline herhangi bir agent'ta çalışabilir

    stages {
        // 1. Aşama: Kodu GitHub'dan Çek
        stage('Checkout') {
            steps {
                // GitHub'dan en güncel kodu klonla
                git url: 'https://github.com/muhammedkayag/jenkins-projem.git', branch: 'main'
                echo 'Kod başarıyla çekildi.'
            }
        }

        // 2. Aşama: Dosyaları Kopyala (Deploy)
        stage('Deploy') {
            steps {
                script {
                    // Jenkins, kodları kendi workspace'ine çeker.
                    // Bu workspace'ten dosyaları Nginx'in yayın dizinine kopyalıyoruz.
                    // SSH yok, scp yok, sadece basit bir 'cp' komutu!
                    echo "Dosyalar /var/www/html/ dizinine kopyalanıyor..."
                    sh 'cp -R * /var/www/html/'
                    echo "Kopyalama tamamlandı!"
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline başarıyla tamamlandı!'
        }
        failure {
            echo 'Pipeline bir hata ile sonlandı!'
        }
    }
}
