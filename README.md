# Fix change HDA Intel Driver to able using headset black jack connector on ASUS S46C laptop. 

Fix problem when using headset(headphone+mic) jack wire. 

I hope help someone that have the same problem with me using headset in this laptop. So lets fix it.

1. You need install alsamixer tools to change some pins hardware functionality. So put this command on terminal:
```
sudo apt-get update
sudo apt-get install alsa-tools-gui
```
2. After this you need edit the file alsa-base.conf, adding the following command line in the ending of file:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=alc255-asus
```
The only model that works for my ALC270 module was the "alc255-asus" model.
After this, the option headset shows when I plugged the headset on laptop.

3. After this you need to use the program hdajackretask and select the Realtek ALC270 coded, and click in the option "Show unconnected pins" and you need to mark the pin ID "0x1a" to be "Headphone" and the pin ID "0x18" to be "Microphone"

4. After this, you need reboot the ubuntu. 

Obs: if alc255-asus don't works for you, you can try another options, like: alc269-dmic, alc271-dmic, headset-mic, alc283-headset. Don't forget to restart the machine after hdajackretask.
