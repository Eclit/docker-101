
# Faydalı Docker Komutları

Bu dosyada en çok kullanılan Docker komutları, örnekleri ve kullanılan flag'lerin açıklamaları gruplara ayrılmış şekilde yer almaktadır. Dilediğiniz zaman kopya çekebilirsiniz!

---

## Genel Bilgi

```
docker --version
```
**Açıklama:** Yüklü Docker sürümünü gösterir.

---

## İmajlar

```
docker images
```
**Açıklama:** Yerel sistemdeki Docker imajlarını listeler.
- `-a` veya `--all`: Tüm imajları gösterir.

```
docker build -t myimage:latest .
```
**Açıklama:**  (Eğer varsa) Dockerfile ile imaj oluşturur.
- `-t`: İmaj adı ve etiketi belirtir.
- `.`: Dockerfile'ın bulunulan dizinde olduğunu belirtir 

```
docker pull ubuntu:latest
```
**Açıklama:** Docker Hub'dan imaj indirir.

```
docker rmi nginx
```
**Açıklama:** Belirtilen imajı siler.
- `-f`: Zorla siler.

---

## Konteyner Yönetimi ve docker run

```
docker ps
```
**Açıklama:** Çalışan konteynerleri listeler.
- `-a` veya `--all`: Tüm (çalışan ve durdurulmuş) konteynerleri gösterir.
- `-q`: Sadece konteyner ID'lerini gösterir.

```
docker run -d -p 8080:80 --name webserver nginx
```
**Açıklama:** İmajdan yeni bir konteyner başlatır.
- `-d`: Arka planda çalıştırır.
- `-p`: Port yönlendirmesi yapar.
- `--name`: Konteynere isim verir.
- `-it`: Etkileşimli terminal açar.

```
docker stop webserver
```
**Açıklama:** Konteyneri durdurur.

```
docker start webserver
```
**Açıklama:** Durdurulmuş bir konteyneri tekrar başlatır.

```
docker rm webserver
```
**Açıklama:** Konteyneri siler.
- `-f`: Zorla siler.

```
docker restart webserver
```
**Açıklama:** Konteyneri yeniden başlatır.

```
docker exec -it webserver bash
```
**Açıklama:** Konteynerde komut çalıştırır, etkileşimli terminal açar.

```
docker inspect webserver
```
**Açıklama:** Konteynerin detaylı durumunu ve yapılandırmasını gösterir.

---

## Loglar

```
docker logs webserver
```
**Açıklama:** Konteynerin çıktısını/loglarını gösterir.
- `-f` veya `--follow`: Logları canlı takip eder.
- `--tail N`: Son N satırı gösterir.

```
docker logs --follow webserver
```
**Açıklama:** Logları canlı olarak izler.


---






## Depolama

### Volume
```
docker volume ls
```
**Açıklama:** Docker volume'larını listeler.

```
docker run -v myvolume:/container/data nginx
```
**Açıklama:** Docker volume'u konteynerde belirli bir yol olarak bağlar. Volume'lar veri kalıcılığı için kullanılır.

### Bind Mount (Klasör/Dosya Bağlama)
```
docker run -v /host/path:/container/path nginx
```
**Açıklama:** Host makinedeki bir klasörü konteynerde belirli bir yol olarak bağlar.

```
docker run -v /host/file.txt:/container/file.txt nginx
```
**Açıklama:** Host'taki bir dosyayı konteynerde belirli bir dosya olarak bağlar.

---

## Network

```
docker network ls
```
**Açıklama:** Docker ağlarını listeler.

```
docker network create mynetwork
```
**Açıklama:** Yeni bir ağ oluşturur.

```
docker run -d --name webserver --network mynetwork nginx
```
**Açıklama:** Konteyneri belirli bir ağa bağlı şekilde başlatır.

```
docker network connect mynetwork webserver
```
**Açıklama:** Çalışan bir konteyneri mevcut bir ağa ekler.



---

## Docker Compose

```
docker-compose up -d
```
**Açıklama:** docker-compose.yml dosyasındaki servisleri arka planda başlatır.
- `-d`: Arka planda çalıştırır.

```
docker-compose down
```
**Açıklama:** Tüm servisleri ve bağlı ağları durdurur ve siler.




## Diğer

```
docker system prune -a
```
**Açıklama:** Kullanılmayan tüm objeleri (imaj, konteyner, ağ, volume) siler.
- `-a`: Tüm kullanılmayan imajları da siler.



