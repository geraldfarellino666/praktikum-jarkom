# LAPORAN PRAKTIKUM JARKOM
## MODUL 7 TCP
## Tujuan Praktikum
1. Mahasiswa bisa membuat program berbasis socket UDP
2. Mahasiswa bisa membuat program berbasis socket TCP

## Langkah Kerja
1. Mempersiapkan lingkungan Python pada VS Code.
2. Membuat file UDPServer.py dan UDPClient.py. Jalankan server terlebih dahulu, lalu kirim pesan teks dari client.
3. Membuat file TCPServer.py dan TCPClient.py. Amati proses inisiasi koneksi sebelum data ditransfer.
4. Melakukan pengujian Multiple Clients pada kedua protokol untuk melihat perbedaan penanganan antrian.
5. Mendokumentasikan hasil eksekusi terminal dan menganalisis perbedaan teknisnya.

## Hasil dan Analisis Praktikum
**Kode Program UDP Server**
```python
from socket import *

serverPort = 12000
serverSocket = socket(AF_INET, SOCK_DGRAM)
serverSocket.bind(('', serverPort))

print("The server is ready to receive")

while True:
message, clientAddress = serverSocket.recvfrom(2048)
modifiedMessage = message.decode().upper()
serverSocket.sendto(modifiedMessage.encode(), clientAddress)
```

**Penjelasan Alur Program**
- Inisialisasi: Server membuat socket dengan tipe SOCK_DGRAM (UDP) dan melakukan bind ke port 12000.
- Proses: Server masuk ke dalam infinite loop untuk menunggu paket. Karena UDP connectionless, server tidak perlu menerima koneksi, melainkan langsung membaca data dan alamat pengirim menggunakan recvfrom().
- Output: Data diubah menjadi huruf kapital (uppercase) lalu dikirim balik ke alamat client yang spesifik menggunakan sendto().

**Kode Program UDP Client**

```python
from socket import *

serverName = 'localhost'
serverPort = 12000

clientSocket = socket(AF_INET, SOCK_DGRAM)
message = input('Input lowercase sentence: ')
clientSocket.sendto(message.encode(), (serverName, serverPort))

modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
print(modifiedMessage.decode())

clientSocket.close()
```