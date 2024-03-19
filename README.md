# Custom Windows Server Image : Auto Installer

---

## 1. Download & Setup Installer :

```jsx
wget https://raw.githubusercontent.com/rennode/Custom-Windows-Server-Image/main/windows-server-autoinstaller.sh && chmod +x windows-server-autoinstaller.sh && ./windows-server-autoinstaller.sh
```

## 2. Run QEMU :

Note - Ubah xxx sesuai dengan versi windows yang kalian pilih.

```jsx
qemu-system-x86_64 \
-m 3G \
-cpu host \
-enable-kvm \
-boot order=d \
-drive file=windows2xxx.iso,media=cdrom \
-drive file=windows2xxx.img,format=raw,if=virtio \
-drive file=virtio-win.iso,media=cdrom \
-device usb-ehci,id=usb,bus=pci.0,addr=0x4 \
-device usb-tablet \
-vnc :0 \
```

## 3. Akses via VNC :

Buka RealVNC Viewer, masukkan IP VPS kalian. Setelah itu ikuti langkah langkah yang ada di video.

## 4. Download File Custom Windows Server Kalian :

Download dan simpan file custom ini biar ga perlu ngulang dari awal lagi kalo mau create rdp.

Ubah xxx sesuai dengan versi Windows Server kalian.

```jsx
dd if=windows2xxx.img | gzip -c>windows2xxx.gz
apt install apache2
sudo ufw allow 'Apache'
cp windowsxxx.gz /var/www/html/
```

kemudian buka browser untuk download filenya.

ubah yyy.yyy.yyy dengan IP VPS kalian dan xxx sesuai dengan versi Windows Server kalian.

```jsx
http://yyy.yyy.yyy/windows2xxx.gz
```

## 5. Setting Agar Bisa Diakses via RDP :

Create droplet baru dan ikuti petunjuk yang ada di YouTube

```jsx
wget -O- --no-check-certificate http://yyy.yyy.yyy/windowsxxxx.gz | gunzip | dd of=/dev/vda
```
