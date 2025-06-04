# Setting Up ILI9341 on Raspberry Pi 3 with fbcp-ili9341

## **1️⃣ Wiring the ILI9341 to Raspberry Pi 3**

Connect the ILI9341 display to the Raspberry Pi 3 as follows:

|ILI9341 Pin|Raspberry Pi 3 GPIO|
|---|---|
|VCC|3.3V (Pin 1)|
|GND|GND (Pin 6)|
|CS|GPIO 8 (Pin 24)|
|RESET|GPIO 25 (Pin 22)|
|DC|GPIO 24 (Pin 18)|
|MOSI|GPIO 10 (Pin 19)|
|SCK|GPIO 11 (Pin 23)|
|MISO|GPIO 9 (Pin 21)|
|LED|3.3V (Pin 17)|

---

## **2️⃣ Enable SPI on Raspberry Pi**

1. Open the Raspberry Pi configuration tool:
    
    ```sh
    sudo raspi-config
    ```
    
2. Navigate to **Interfacing Options > SPI** and enable it.
3. Reboot the system:
    
    ```sh
    sudo reboot
    ```
    
4. Verify SPI is enabled:
    
    ```sh
    ls /dev/spi*
    ```
    

---

## **3️⃣ Install fbcp-ili9341**

1. Install required dependencies:
    
    ```sh
    sudo apt update
    sudo apt install cmake git libraspberrypi-dev
    ```
    
2. Clone the `fbcp-ili9341` repository:
    
    ```sh
    git clone https://github.com/juj/fbcp-ili9341.git
    cd fbcp-ili9341
    mkdir build
    cd build
    ```
    
3. Compile fbcp-ili9341:
    
    ```sh
    cmake .. -DSPI_BUS_CLOCK_DIVISOR=8 -DILI9341=ON -DUSE_DMA_TRANSFERS=ON -DGPIO_TFT_DATA_CONTROL=24 -DGPIO_TFT_RESET_PIN=25
    make -j$(nproc)
    sudo install fbcp-ili9341 /usr/local/bin/
    ```
    

---

## **4️⃣ Test fbcp-ili9341**

Run the following command to check if the display works:

```sh
sudo fbcp-ili9341
```

If the screen turns on and displays content, proceed to the next step.

---

## **5️⃣ Auto-start fbcp-ili9341 at Boot**

1. Open the `rc.local` file:
    
    ```sh
    sudo nano /etc/rc.local
    ```
    
2. If the file is empty, add the following content:
    
    ```sh
    #!/bin/bash
    # rc.local script to start programs at boot
    
    # Print the date to a log file (optional)
    echo "Booting at $(date)" >> /home/pi/boot_log.txt
    
    # Start fbcp-ili9341
    /usr/local/bin/fbcp-ili9341 &
    
    # Exit with success
    exit 0
    ```
    
3. Save and exit (`CTRL + X`, then `Y`, then `Enter`).
4. Make the script executable:
    
    ```sh
    sudo chmod +x /etc/rc.local
    ```
    
5. Reboot the system:
    
    ```sh
    sudo reboot
    ```
    

---

## **6️⃣ Verify Everything is Working**

After reboot, check if `fbcp-ili9341` is running:

```sh
ps aux | grep fbcp-ili9341
```

If the screen is not displaying anything, check SPI status:

```sh
dmesg | grep spi
```

---

## **🎉 Done!**

Your ILI9341 display should now be working with Raspberry Pi 3 using `fbcp-ili9341`. 🚀