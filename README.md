
# DATABASE_PEMINJAMAN_RUANG_KELAS
## **DDL Script**

```sql
SHOW DATABASES;
```

```sql
CREATE DATABASE peminjaman_ruang_kelas;
```

```sql
USE peminjaman_ruang_kelas;
```

```sql
SHOW TABLES;
```

```sql
DESC gedung;
```

```sql
DESC ruang_kelas;
```

```sql
DESC jdwl_penggunaan_ruang;
```

```sql
DESC transaksi_peminjaman;
```

```sql
DESC peminjam;
```

```sql
CREATE TABLE gedung (
    id_gedung VARCHAR(10) PRIMARY KEY NOT NULL,
    nama VARCHAR(45) NOT NULL,
    kapasitas INT(5),
    lokasi VARCHAR(45) NOT NULL
);
```

```sql
CREATE TABLE ruang_kelas (
    id_ruang VARCHAR(10) PRIMARY KEY NOT NULL,
    id_gedung VARCHAR(10),
    nama VARCHAR(45) NOT NULL,
    kapasitas INT(5)
);
```

```sql
CREATE TABLE jadwal_penggunaan_ruang (
    id_jadwal VARCHAR(10) PRIMARY KEY NOT NULL,
    id_ruang VARCHAR(10),
    tanggal DATE,
    waktu_mulai TIME,
    waktu_selesai TIME
);
```

```sql
CREATE TABLE `transaksi_peminjaman` (
    id_transaksi varchar(10) NOT NULL,
    id_jadwal varchar(10) DEFAULT NULL,
    id_peminjam varchar(10) DEFAULT NULL,
    status varchar(15) NOT NULL,
    tgl_peminjaman datetime DEFAULT NULL
);
```

```sql
CREATE TABLE peminjam (
    id_peminjam VARCHAR(10) PRIMARY KEY NOT,
    nama VARCHAR(10) NOT NULL,
    no_hp VARCHAR(15) NOT NULL,
    email VARCHAR(100)
);
```

```sql
CREATE TABLE laporan_transaksi (
    id_laporan VARCHAR(10) PRIMARY KEY NOT,
    id_transaksi VARCHAR(10),
    tanggal DATETIME NOT NULL,
    keterangan VARCHAR(45)
);
```

```sql
ALTER TABLE ruang_kelas
ADD CONSTRAINT fk_gedung_ruang_kelas
FOREIGN KEY (id_gedung) REFERENCES gedung(id_gedung);
```

```sql
ALTER TABLE jdwl_penggunaan_ruang
ADD CONSTRAINT fk_jdwl_ruang
FOREIGN KEY (id_ruang) REFERENCES ruang_kelas(id_ruang);
```

```sql
ALTER TABLE transaksi_peminjaman
ADD CONSTRAINT fk_jdwl_transaksi_peminjaman
FOREIGN KEY (id_jadwal) REFERENCES jdwl_penggunaan_ruang(id_jadwal);
```

```sql
ALTER TABLE transaksi_peminjaman
ADD CONSTRAINT fk_peminjam_transaksi_peminjaman
FOREIGN KEY (id_peminjam) REFERENCES peminjam(id_peminjam);
```

```sql
ALTER TABLE laporan_transaksi
ADD CONSTRAINT fk_transaksi_laporan
FOREIGN KEY (id_transaksi) REFERENCES laporan_transaksi(id_transaksi);
```

```sql
ALTER TABLE gedung MODIFY nama VARCHAR(10) NOT NULL;
```

```sql
ALTER TABLE ruang_kelas CHANGE jumlah kapasitas INT(5);
```

```sql
ALTER TABLE ruang_kelas DROP lokasi;
```
