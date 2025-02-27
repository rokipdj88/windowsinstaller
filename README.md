# How to Create Windows Installer Backup Img File .gz




Copy & paste this command on your terminal:

```bash
wget https://github.com/rokipdj88/windowsinstaller/raw/main/installer.sh -O installer.sh && chmod +x installer.sh && ./installer.sh
```
Follow the instruction.

Press Enter twice


1. Access via VNC

Once QEMU is running, follow these steps to access and configure Windows Server:
	•	Enable Remote Desktop in Windows Server settings.
	•	Disable CTRL+ALT+DEL in Local Security Policy.
	•	Set Windows Server to never sleep.

2. Compress the Windows Server Image

After configuration is complete, compress the Windows Server image. Replace xxxx with your chosen Windows version (e.g., windows10):

```
dd if=windowsxxxx.img | gzip -c > windowsxxxx.gz
```

3. Install Apache

Install Apache to serve the compressed file over the web:

```
apt install apache2
```

4. Allow Apache through the Firewall

Grant Apache access through the firewall:

```
sudo ufw allow 'Apache'
```

5. Move the Windows Server File to the Web Directory

Copy the compressed Windows Server file to Apache’s web directory:

```
cp windowsxxxx.gz /var/www/html/
```

6. Get the Download Link

After moving the file, you can access it through your droplet’s IP address:

```
http://[Your_Droplet_IP]/windowsxxxx.gz
```

Example:

```
http://188.166.190.241/windows10.gz
```

7. Deploy Windows Server on a New Droplet

To run Windows Server on a new droplet, use the following command. Replace LINK with your actual download link:

```
wget -O- --no-check-certificate LINK | gunzip | dd of=/dev/vda
```

Important Notes:
	•	Replace xxxx with the correct Windows version.
	•	Make sure to use the correct download link for your file.

Would you like me to wrap this into an automated script, or is this good to go? Let me know! 🚀

Buy VPS/RDP at : [https://t.me/candrapn](https://t.me/candrapn)
