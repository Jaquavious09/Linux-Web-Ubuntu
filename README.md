# Linux-Web-Ubuntu
Step 1: Install XFCE4

XFCE is a lightweight desktop environment. Run:

sudo apt update
sudo apt install xfce4 xfce4-goodies -y


xfce4: main desktop environment

xfce4-goodies: optional extra apps and plugins

Step 2: Install TigerVNC

TigerVNC will provide the VNC server:

sudo apt install tigervnc-standalone-server tigervnc-common -y

Step 3: Set VNC password

Run the VNC server once to set a password:

vncpasswd


Enter a password (6–8 characters recommended)

Optionally set a view-only password

Step 4: Configure VNC session

Create or edit the startup script for VNC:

mkdir -p ~/.vnc
nano ~/.vnc/xstartup


Paste the following:

#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &


Make it executable:

chmod +x ~/.vnc/xstartup

Step 5: Start the VNC server

Run:

vncserver :1 -geometry 1920x1080 -depth 24


:1 → display number

-geometry → resolution

-depth → color depth

Check that it started:

vncserver -list

Step 6: Install noVNC

Clone noVNC repository:

git clone https://github.com/novnc/noVNC.git
cd noVNC


Also install WebSockets proxy (websockify):

git clone https://github.com/novnc/websockify.git

Step 7: Start noVNC

Run noVNC to serve your VNC session:

./utils/novnc_proxy --vnc localhost:5901

Copy and paste everything if needed!

Starting the server for the first time:
vncserver

Killing the server:
vncserver -kill :1

Starting a new server (basic reboot):
vncserver :1

Install dependencies for noVNC (Only do it if they are missing!):
sudo apt install -y git python3-websockify

Clone the noVNC repository (Only do it if they are missing!):
git clone https://github.com/novnc/noVNC.git ~/noVNC

Navigate to the noVNC folder:
cd ~/noVNC

cd ~
wget -O firefox.tar.xz "https://download.mozilla.org/?product=firefox-latest&os=linux64&lang=en-US"
tar -xf firefox.tar.xz
mv firefox ~/firefox-latest

Start the noVNC server::
./utils/novnc_proxy --vnc localhost:5901
