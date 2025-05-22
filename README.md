# Vlog Waydroid

1. Ubuntu Wayland
2. Install dari repository
3. Inisialisasi Waydroid, VANILLA (F-Droid) atau GAPP? pilih GAPP, proses download
4. Daftarkan Android device-nya


### Ubuntu Wayland

Pastikan sudah install wayland

```
sudo nano /etc/gdm3/custom.conf
```

Enable Wayland
```
WaylandEnable=true
```

Restart GDM3
```
sudo systemctl restart gdm3
```


### Install di Ubuntu

Referensi: https://docs.waydro.id/usage/install-on-desktops


```
sudo apt install curl ca-certificates -y
curl -s https://repo.waydro.id | sudo bash
sudo apt install waydroid -y
```

### Daftarkan Google Play utk device tsb

Referensi: https://docs.waydro.id/faq/google-play-certification

```
sudo waydroid shell
ANDROID_RUNTIME_ROOT=/apex/com.android.runtime ANDROID_DATA=/data ANDROID_TZDATA_ROOT=/apex/com.android.tzdata ANDROID_I18N_ROOT=/apex/com.android.i18n sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"
```

Masukkan ID di link berikut: https://www.google.com/android/uncertified


# Troubleshooting

Start container:
```
sudo waydroid container Start
```

Start session:
```
waydroid session start
```

Full-screen mode:
```
waydroid show-full-ui
```

Multi-window mode:
```
waydroid prop set persist.waydroid.multi_windows true
waydroid session stop
waydroid session start
```

How to remove Waydroid on Ubuntu 22.04 | Reinstalling Waydroid on Ubuntu 22.04. Sometimes things don't go as planned and you need to remove it all and start over. To do that, follow the steps below:
...
sudo waydroid session stop
...
udo waydroid container stop
...
sudo apt remove waydroid
...
sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid ~/.share/waydroid ~/.local/share/applications/*aydroid* ~/.local/share/waydroid
...
