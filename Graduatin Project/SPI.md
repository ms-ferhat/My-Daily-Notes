
### Enable 
```
sudo raspi-config
--> interface options --> spi

sudo reboot
```

__Check SPI enable__
```
ls /dev/spi
```

__Check Load module__
```
lsmod | grep spi
```



![[Pasted image 20250308163836.png]]