# Steps to set up bauh on a Debian-base Linux system

NOTE: This is an instructional page to set up Bauh on most Debian-based systems. Original project is at https://github.com/vinifmor/bauh.

### **1. Create folder to set up bauh in**  

    mkdir ~/Softwares

### **2. Install packages that are needed for the set up**  
    
    sudo apt install snapd
    sudo apt install flatpak
    sudo apt install python3
    sudo apt install python3-pip
    sudo apt install python3-requests
    sudo apt install python3-yaml
    sudo apt install qt5dxcb-plugin libqt5svg5 python3-pyqt5.qtsvg
    sudo apt install python3-venv
    sudo apt install libappindicator _(for tray icon, might not be needed on some systems)_

### **3. Now we set up the python environment to install bauh in**

    cd ~/Softwares
    python3 -m venv bauh_env
    bauh_env/bin/pip3 install --upgrade pip
    bauh_env/bin/pip3 install bauh

### **4. Now we set up the icon for for the system to launch bauh**

    cd ~/.local/share/applications
    touch bauh.desktop

 - Insert this into the bauh.desktop file

        [Desktop Entry]
        Type=Application
        Name=bauh
        Comment=Install and remove applications ( AppImage, AUR, Flatpak, Snap )
        Exec=/home/$USER/Softwares/bauh_env/bin/bauh
        Icon=/home/$USER/Softwares/bauh_env/lib/python3.9/site-packages/bauh/view/resources/img/logo.svg

### **5. Now we add AppImage support for bauh**

    sudo apt install sqlite3
    sudo apt install wget
    sudo apt install aria2
    touch ~/.config/bauh/appimage.yml

### **6. Now we add Web support for bauh**

    ~/Softwares/bauh_env/bin/pip3 install beautifulsoup4
    ~/Softwares/bauh_env/bin/pip3 install lxml
    npm install electron -g
    npm install nativefier -g

## Note:
- To update bauh

        ~/Softwares/bauh_env/bin/pip3 install --upgrade pip && ~/Softwares/bauh_env/bin/pip3 install --upgrade bauh

- To remove bauh

        rm -rf ~/Softwares/bauh_env
