# PEMROGRAMAN ASSEMBLY DENGAN DEBUG

Repositori ini berisi dokumentasi dan hasil praktikum pemrograman Assembly menggunakan utilitas DEBUG di lingkungan emulator DOSBox.

## Install DOSBOX

<div align="center">
<a href="https://www.dosbox.com/download.php?main=1">
  <img src="https://www.dosgames.com/blogimgs/dosbox-banner.png" alt="DOSBOX Banner" />
</a>
</div>

---

## Kemudian Download DEBUG

Program `DEBUG.COM` tidak disertakan dalam DOSBox atau Windows modern. Kalian bisa unduh file `DEBUG.COM` dari sumber terpercaya misalnya di **FreeDOS**

<a href="https://www.freedos.org/download/">Download DEBUG di **FreeDOS**</a> atau tinggal Download `DEBUG.zip` di Page ini.

Setelah diunduh, file berupa `.zip` kalian Extract dan taruh di folder kalian, misalnya `C:\PRAK`.

## Cara Menggunakan DOSBox

Buka DOSBox, lalu lakukan mounting folder kalian `C:\PRAK` sebagai drive virtual C: di DOSBox.

```bash
Z:\>mount c c:\PRAK  <-- Sesuaikan dengan path folder kalian
Drive C is mounted as local directory C:\PRAK\

Z:\>c:
C:\>
```

Kemudian jika `DEBUG.com` sudah ada di folder yang di tuju, `C:\PRAK` kalian bisa lansung menjalakannya. Kalau tidak ada Download dulu `DEBUG.COM`.

```bash
C:\>debug
-  <-- Jika Output= ILLEGAL COMMAND: DEBUG. Path anda salah arahkan ke folder BIN tempat DEBUG.com berada
```

```bash
C:\>cd bin
C:\BIN>debug
-   <-- Tanda sudah berhasil
```

## Langkah-Langkah Praktikum (di dalam DEBUG)

```bash
# Mounting program ke local C
mount c c:/

# Masuk partisi C
c:

# Masuk ke direktori tempat lokasi, DEBUG.com
cd prak/BIN

DEBUG

a100
```

Ketikkan program

```bash
MOV ax,05
Mov ds,ax
Mov si,012
Mov di,021
Mov ax,si
Mov di,ax
int 20
```

Kemudian kalian bisa, tekan `ENTER`

```bash
-t
```

Menyimpan program

```bash
-n try.com

-w
Writing 0000 bytes
```

## Langkah Praktik 2

Latihan menulis, menghitung panjang program, memberi nama, menyimpan program, memberi nama dan menjalankan program.

Ketikkan program

```bash
Mov ah,02
Mov dl,41
Int 21
Int 20
```

Tekan `ENTER`, sekarang menentukan panjang program

```bash
rcx
8
n prak5.com
w
g # Menampilkanm hasil berupa huruf A
q
```

## KUIS

```bash
# Cara menghapus data pada register:

MOV dl,08
int 21

# Cara membuat spasi pada register:

MOV dl,5f
int 21

```

---

## POSTEST

Membuat program `1NF0RMATIKA _U4D` dengan menggunakan TABEL ASCII

<div align="center">
<a href="https://www.geeksforgeeks.org/dsa/ascii-table/">
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240304094301/ASCII-Table-660.png" alt="ASCII Table Image"/>
</a>
</div>

Kode program **POSTEST** dengan tabel `ASCII` gunakan `HEXADECIMAL`

```bash
a 100
mov ah,02
mov dl,31    ; '1' = 0x31
int 21
mov dl,4E    ; 'N' = 0x4E
int 21
mov dl,46    ; 'F' = 0x46
int 21
mov dl,30    ; '0' = 0x30
int 21
mov dl,49    ; 'I' = 0x49
int 21
mov dl,41    ; 'A' = 0x41
int 21
mov dl,20    ; spasi = 0x20
int 21
mov dl,5F    ; '_' = 0x5F
int 21
mov dl,55    ; 'U' = 0x55
int 21
mov dl,34    ; '4' = 0x34
int 21
mov dl,44    ; 'D' = 0x44
int 21

mov dl,0D
int 21
mov dl,0A
int 21

mov ax,4C00
int 21
[ENTER]
```

Kemudian RCX

```bash
RCX
n inf.com
w
g
```

**NOTE**

- MOV AH,02 — pilih layanan DOS untuk "tulis 1 karakter ke layar".
- MOV DL,xx — letakkan kode ASCII karakter yang mau dicetak (xx dalam hex atau pakai 'A').
- INT 21 — panggil layanan DOS; bila AH=02, isi DL akan dicetak.

`Urutan wajib`: set AH → set DL → INT 21.

---
