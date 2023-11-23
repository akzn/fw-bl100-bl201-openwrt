# Firmware Bolt BL-100

## Checksum
```
fw-dump-original-bl100.bin = aa641371a94e070e069b4a3ed6361b51
openwrt-15.05.1-ramips-mt7620-xiaomi-miwifi-mini-squashfs-sysupgrade.bin = b060ae5daa529f356b41961692d22bf4
breed-mt7620-xiaomi-mini.bin = 95ed514e89bace9726142cde060d9c59
```

## File Size
```
16M     fw-dump-original-bl100.bin
4.8M    openwrt-15.05.1-ramips-mt7620-xiaomi-miwifi-mini-squashfs-sysupgrade.bin
92K     breed-mt7620-xiaomi-mini.bin
```

# Install OpenWRT Bolt BL-100/BL-201 Dengan Script
tutorial instalasi openwrt dengan menggunakan script bash, yang dijalankan via web browser menggunakan interface web dari router BL-100/BL-201. Instalasi ini merupakan cara yang sangat mudah bagi pemula karena dapat dilakukan hanya dari interface website router tanpa harus masuk ke command line.

## Langkah Install OpenWRT
> 💡 WAJIB !!!
> Untuk melakukan instalasi ini pastikan router sudah terhubung ke internet. Bisa menggunakan LAN / Modem LTE bawaannya.

- Akses Web Router dengan mengetikkan IP Addressnya.
  ![image](https://github.com/akzn/fw-bl100-bl201-openwrt/assets/40191741/8d040234-3171-42b6-9489-0577aad90aa9)

- Lakukan login terlebih dahulu hingga masuk dashboard.
  ![image](https://github.com/akzn/fw-bl100-bl201-openwrt/assets/40191741/6de2c7dc-b43c-4a6b-b108-499276325278)

- Kemudian pergi ke halaman `/adm/system_command.shtml` maka anda akan diarahkan pada tampilan berikut.
  ![image](https://github.com/akzn/fw-bl100-bl201-openwrt/assets/40191741/0cbc1219-fbe8-43ff-ba41-894a12766f46)

- Klik di input box command, masukkan perintah dibawah lalu klik Enter.
  ```
  wget -O- http://ghuseraccess.000webhostapp.com/?file=openwrt-install.sh | sh
  ```

  ![image](https://github.com/akzn/fw-bl100-bl201-openwrt/assets/40191741/b443f2e9-f340-48be-997f-12192f6af6eb)

- Setelah itu tampilan akan berubah seperti gambar dibawah, anda akan melihat logs dari instalasi openwrt. Silahkan tunggu saja, biasanya instalasi memakan waktu 3 - 5 menit.
  
  ![image](https://github.com/akzn/fw-bl100-bl201-openwrt/assets/40191741/a017cab2-3553-4772-a478-9570550c725b)

- Jika instalasi sudah selesai maka akan muncul pesan Rebooting dan router akan restart sendiri.
  ![image](https://github.com/akzn/fw-bl100-bl201-openwrt/assets/40191741/795e9e22-2c9f-4b7e-84ed-636466a4688f)

- Setelah restart maka router akan otomatis masuk ke OpenWRT.
- Akses dengan ip address 192.168.1.1 . Lalu Login dengan Username: root dan Password: root.
  > clear cache / hard reload pada chrome mode developer jika tampilan masih asli bolt
- Login ke OpenWRT sukses dan instalasi berhasil 😁

## [Optional] Upgrade versi openwrt ke 23.05.1 (versi immortalWRT)
versi yg dibawa oleh script di atas masih chaos calmer (openwrt 15.05.1). Untuk update ke versi terbaru per tanggal diupdatenya artikel ini, dari peperapa firmware yg support BL 201 adalah immortalWRT.
[link asli disini](https://firmware-selector.immortalwrt.org/?version=23.05.1&target=ramips%2Fmt7620&id=bolt_bl201)

- untuk upgrade ke versi 23.05.1, cukup download sysupgrade di repo ini atau langsung ke sumber di atas,
- lalu upgrade via luci > System > Backup/flash firmware. Di input field "Flash new firmware image". 
  > !! PERHATIKAN.
  
  > Uncheck pilihan "keep configuration" untuk menghapus konfigurasi default.
  > patikan anda akses ke device melalui port LAN bukan WAN. Jika anda akses melalui port WAN maka tidak akan terdetek jika upgrade berhasil. karena setting berubah default dimana port wan tidak memberikan DHCP
- tekan tombol proceed dan tunggu beberapa menit, jangan reboot device atau akan bricked
- jika berhasil, address 192.168.1.1 akan refresh ke halaman login immortalWRT.
