# Tugas-NetPro-9
# Anggota Kelompok : 
Meilyand Evriyan Timor (1301161769)  
Reyhan Rahmansyah (1301160805)  
Reno Butar Butar (1301164724)  

# PHPloy 
PHPloy merupakan tools untuk mendeploy aplikasi atau kodingan ke server. PHPloy ini menggunakan Git sebagai code collaboration. Konsep kerja PHPloy ini adalah melakukan perubahan (upload/delete) file-file yang telah tercommit pada git ke server.

# Penggunaan PHPloy
Untuk memulai menggunakan PHPloy anda bisa mengikuti langkah-langkah berikut ini:  
1. Gunakan composer dengan menambah paket di file composer.json.  
```
{
    "require": {
        "banago/phploy":"4.8.5"
    }
}
```  
2. Selanjutnya dari terminal jalankan perintah:  
```
composer update
```  
3. Copykan file /vendor/banago/phploy/bin/phploy ke root project  
4. Buat file baru dengan nama phploy.ini, yang berisi kode konfigurasi berikut  
```
[production]
user = username
pass = s0m3p455w0rd
host = yourdomain.com
path = /public_html/folder
exclude[] = 'phploy'
exclude[] = 'phploy.ini'
exclude[] = 'composer.json'
exclude[] = 'composer.lock'
port = 21
passive = true
```  
5. Setelah itu cek apakah phploy dan konfigurasinya sudah sesuai dengan menjalankan perintah di terminal  
```
./phploy -v
```  
6. Setelah melakukan perubahan kode-kode program, jalankan perintah git add dan git commit  
7. Untuk melihat file-file apa saja yang akan di deploy, gunakan perintah berikut di terminal  
```
./phploy -l
```  
8. Dan untuk proses deploy ketikan perintah phploy  
```
./phploy
```  

# Stack Up (sup)
Stack up merupakan tool deployment sederhana yang dapat memberikan set perintah dalam beberapa host yang pararel. Stack Up membaca Supfile, sebuah file konfigurasi YAML yang mendefinisikan networks (kumpulan host),perintah-perintah, dan targetnya.

# Penggunaan sup
1. Instalasi  
Ketik ``` $ go get -u github.com/pressly/sup/cmd/sup ``` pada terminal  
2. Network
```
networks:
    production:
        hosts:
            - api1.example.com
            - api2.example.com
            - api3.example.com
    staging:
        # fetch dynamic list of hosts
        inventory: curl http://example.com/latest/meta-data/hostname
 ```  
 $ sup production COMMAND akan menge-run COMMAND pada api1, api2 and api3 hosts.  
 
 3. Shell command
 ```
 commands:
    restart:
        desc: Restart example Docker container
        run: sudo docker restart example
    tail-logs:
        desc: Watch tail of Docker logs from all hosts
        run: sudo docker logs --tail=20 -f example
 ```  
$ sup staging restart akan me-restart semua staging Docker containers.

$ sup production tail-logs  

4. Run sup
Gunakan perintah ``` $ sup production deploy ``` untuk menjalankan sup.
