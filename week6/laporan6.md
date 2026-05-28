# LAPORAN PRAKTIKUM JARKOM
## MODUL 6 TCP
## Tujuan Praktikum
Mahasiswa dapat menginvestigasi cara kerja protokol TCP menggunakan Wireshark 

## Langkah Kerja
1. Download file alice.txt dari server laboratorium.
2. Buka halaman unggah file di gaia.cs.umass.edu.
3. Jalankan Wireshark capture dan upload file alice.txt.
4. Stop capture dan gunakan filter: tcp && ip.addr == 128.119.245.12.
5. Analisis handshake, segmen data, dan grafik time-sequence.

## Hasil dan Analisis Praktikum
![Gambar 1](../assets/image/gambar%201%20week%206.png)
Berdasarkan capture, parameter identitas koneksi adalah:
- Client IP: 192.168.0.170 (Port: 59805)
- Server IP: 128.119.245.12 (Port: 443 / HTTPS)
![Gambar 2](../assets/image/gambar%202%20week%206.png)
| Field  | Nilai |
|----------|----------|
| Sequence Number   | 0 (relative)   | 
| Flags  | SYN   |
| MSS  | 1460 bytes   |
| Window Scale  | x256   |



