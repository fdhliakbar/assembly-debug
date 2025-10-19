# PEMROGRAMAN ASSEMBLY DENGAN DEBUG

Repositori ini berisi dokumentasi dan hasil praktikum pemrograman Assembly menggunakan utilitas DEBUG di lingkungan emulator DOSBox.

## Install DOSBOX

<div align="center">
<a href="https://www.dosbox.com/download.php?main=1">
  <img src="https://www.dosgames.com/blogimgs/dosbox-banner.png" alt="DOSBOX Banner" />
</a>
</div>

---

## Kemudian Install DEBUG

Program `DEBUG.COM` tidak disertakan dalam DOSBox atau Windows modern. Kalian bisa unduh file DEBUG.COM dari sumber terpercaya misalnya di FreeDOS

<a href="https://www.freedos.org/download/">Install DEBUG di FreeDOS</a> atau tinggal `DEBUG.zip` di Page ini.

Setelah diunduh, letakkan file DEBUG.COM di dalam folder kalian (misalnya, C:\PRAK).


## Cara Menggunakan DOSBox

1. Memulai Sesi dan Mount Drive
Buka DOSBox, lalu lakukan mounting folder kalian (C:\PRAK) sebagai drive virtual C: di DOSBox.

```bash
Z:\>mount c c:\PRAKTIKUM  <-- Ganti C:\PRAKTIKUM dengan jalur folder Anda
Drive C is mounted as local directory C:\PRAK\

Z:\>c:
C:\>  <-- Anda sekarang berada di drive virtual C:
```

2. Memulai Program Debugger
Karena file DEBUG.COM sudah ada di folder C:\PRAKTIKUM, Anda bisa langsung menjalankannya.

```bash
C:\>debug
-  <-- Prompt berubah, Anda sudah masuk ke lingkungan DEBUG.
```

## Langkah-Langkah Praktikum (di dalam DEBUG)

Setelah prompt berubah menjadi -, ikuti langkah-langkah Assembly sesuai modul.

1. Masukkan Program (Assemble Mode)
Ketik perintah A100 untuk memulai mode perakitan (assemble mode), lalu masukkan kode program berikut baris demi baris:

```bash
-a100
xxxx:0100 MOV AH,15
xxxx:0102 MOV AL,4
xxxx:0104 ADD AH,AL
xxxx:0106 MOV AX,1234
xxxx:0109 MOV BX,F221
xxxx:010C ADD AX,BX
xxxx:010E MOV AX,1234
xxxx:0111 MOV BX,9ABC
xxxx:0114 MOV CX,5678
xxxx:0117 MOV DX,DEF0
xxxx:011A ADD CX,DX
xxxx:011C ADC AX,BX
xxxx:011E INC AL
xxxx:011F INT 20
xxxx:0121  <-- Tekan Enter lagi untuk keluar mode A
-
```

2. Melacak dan Menganalisis (Trace Mode)
Ketik T (Trace) berulang kali untuk mengeksekusi satu per satu instruksi dan mencatat perubahan nilai pada register (AX, BX, CX, DX, dll.). Catat hasil perubahan register setelah setiap langkah.

```bash
-t
(Lalu ulangi "t" hingga mencapai INT 20)
```

3. Menyimpan Program ke Disk
Setelah selesai tracing dan Anda berada kembali di prompt -:

Tentukan Ukuran Program (RCX): (Panjang program adalah 21h byte)

```
-rcx
CX 0000
:21
```

Beri Nama File (N):
```bash
-n PROGRAMKU.COM
Tulis ke Disk (W):
```

```bash
-w
Writing 00021 bytes
```

Keluar dari DEBUG (Q):

```bash
-q
C:\>
```

<div align="center">
  <img src="https://i.pinimg.com/originals/39/80/19/39801915efa95200f03a95629ad3d025.gif" alt="Anime banner from K-ON"/>
</div>
