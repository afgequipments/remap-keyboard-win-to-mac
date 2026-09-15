# Remap Keyboard Windows 11 ke Layout Mac

Panduan ini digunakan untuk mengubah tata letak (*layout*) keyboard laptop/PC Windows 11 agar memiliki posisi tombol modifier yang sama dengan keyboard Mac (mode Mac), tanpa menggunakan aplikasi pihak ketiga (*native via Registry*).

---

## Pemetaan Tombol (Windows vs Mac)

Tata letak tombol modifier sebelah kiri bawah secara default:

* **Layout Asli (Windows):** `[Ctrl]` `[Win]` `[Alt]` `[Space]`
* **Target Layout (Mac):** `[Control]` `[Option / Alt]` `[Command]` `[Space]`

### Perubahan Scancode:
* **Left Alt** -> diubah menjadi **Left Windows (Cmd)** (`38,00` -> `5B,E0`)
* **Left Windows** -> diubah menjadi **Left Alt (Option)** (`5B,E0` -> `38,00`)

---

## Langkah Penerapan

### 1. Buat File Registry (`.reg`)
1. Buka teks editor seperti **Notepad**.
2. Salin dan tempelkan kode Registry berikut:

```reg
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,03,00,00,00,5b,e0,38,00,38,00,5b,e0,00,00,00,00
```

3. Simpan file dengan nama `mac_layout.reg`. Pastikan pada bagian *Save as type* pilih **All Files (*.*)**.

### 2. Terapkan Perubahan
1. Klik ganda file `mac_layout.reg`.
2. Pilih **Yes** ketika muncul konfirmasi *User Account Control* dan *Registry Editor*.
3. **Restart** komputer/laptop agar perubahan *Scancode Map* diterapkan oleh sistem.

---

## Mengembalikan ke Layout Default (Reset Remap)

Jika ingin mengembalikan fungsi tombol ke pengaturan standar Windows:

1. Tekan `Win + R`, ketik `regedit`, lalu tekan **Enter**.
2. Buka direktori berikut:
   ```text
   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout
   ```
3. Klik kanan pada nilai **Scancode Map** dan pilih **Delete**.
4. **Restart** komputer/laptop.
