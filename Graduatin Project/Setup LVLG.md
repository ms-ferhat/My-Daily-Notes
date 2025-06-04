# LVGL Project Dependencies

## Required Libraries and Dependencies

Below is a list of all the necessary libraries and tools installed to set up and run LVGL with the ILI9341 display on a Raspberry Pi 3.

### 1. **System Updates & Essential Tools**

Before installing dependencies, ensure your system is up to date:

```sh
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential cmake make
```

### 2. **LVGL and Graphics-Related Libraries**

Install required libraries for LVGL, display drivers, and graphics rendering:

```sh
sudo apt install -y libpng-dev libjpeg-dev libfreetype6-dev libx11-dev libxext-dev libxft-dev libxinerama-dev
```

### 3. **Wayland and X11 (if needed for GUI apps)**

If using LVGL with Wayland or X11, install these additional libraries:

```sh
sudo apt install -y libwayland-dev libxkbcommon-dev wayland-protocols
```

### 4. **SPI and Display Driver Dependencies**

For SPI communication with the ILI9341 display:

```sh
sudo apt install -y libgpiod-dev
```

### 5. **LVGL Library Setup**

Clone and install LVGL:

```sh
git clone  https://github.com/lvgl/lvgl.git 
```

### 6. **Ensure `lv_conf.h` Exists**

If missing, copy the template:

```sh
cp ~/lvgl_lib/lvgl/lv_conf_template.h ~/lvgl_lib/lv_conf.h
```
