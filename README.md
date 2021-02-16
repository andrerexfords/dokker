# dokker
# Task1 
(Membuat WordPress di Docker Container)
gasskeun
pertama menjalankan container mysql/mariaDB
MySQL
menjalankan mysql dengan perintah berikut
 -sudo docker run --name my-db -e MYSQL_ROOT_PASSWORD=manroes71 -d mysql

Jalankan Kontainer WordPress
Selanjutnya, menjalankan container dari image resmi WordPress yang dipetakan ke host port 8080 dan ditautkan ke container database
dengan perintah berikut:
 -sudo docker run --name wordpressgua -p 8080:80 --link my-db:mysql -d wordpress
 
Untuk langkah penginstalan terakhir,kita perlu mengakses container WordPress dari browser.

disni saya memetakan port 8080 pada host ke port 80 (layanan web) pada container. Ini memungkinkan kita untuk mengakses di browser menggunakan alamat IP atau URL server:

http://192.168.100.94/:8080
http://example.com:8080

Menggunakan Docker Compose untuk menjalankan WordPress
Buat File YAML
Pertama, saya membuat direktori task1 dan pindahkan ke dalamnya:
-sudo mkdir task1
-cd task1
membuat file YAML bernama docker-compose.yml
-sudo nano docker-compose.yml
dan memasukkan script berikut
wordpress:
  image: wordpress
  links:
    - wordpress_db:mysql
  ports:
    - 9000:80

wordpress_db:
  image: mysql
  environment:
    MYSQL_ROOT_PASSWORD: manroes71
 Simpan dan keluar dari file. 
Selanjutnya, gunakan Docker Compose untuk menjalankan kontainer ini dengan perintah :
-docker-compose up -d
kita dapat memastikan bahwa kontainer sudah dibuat dengan menggunakan perintah:
-docker-compose ps
dan menjalankan di browser dengan memasukkan url berikut:
http://192.168.100.94:9000/









