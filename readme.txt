********************************************************************************
*        Anleitung zur Verwendung der                                          *
*              Microsoft Xbox 360 Kinect                                       *
********************************************************************************

--------------------------------------------------------------------------------
| 1. Schritt
|    installation der benoetigten Pakete
|
|      // java wird nur benoetigt da im openni paket auch beispiele fuer java 
|      // programme vorliegen, die mit kompiliert werden muessen

sudo apt-get install git build-essential python libusb-1.0.0-dev freeglut3-dev doxygen graphviz mono-complete

sudo apt-get install openjdk-6-jdk openjdk-6-source openjdk-6-demo openjdk-6-doc openjdk-6-jre-headless openjdk-6-jre-lib 

--------------------------------------------------------------------------------
| 2. Schritt
|    download von OpenNi, SensorKinect und NiTE
|        
|      // die Komponenten muessen zueinander passen ansonsten schlaegt
|      // das compilieren oder das installieren fehl, deshalb wird am
|      // besten alles gemeinsam aus dem folgenden Ordner geladen, den ich
|      // vorbereitet habe und gemeinsam in diesem Ordner gespeichert.
|      // https://github.com/matthiasmax/kinect

git clone https://github.com/matthiasmax/kinect.git

--------------------------------------------------------------------------------
| 3. Schritt
|    compilieren und installieren von openni
|       // ausgehend vom "kinect" ordner

cd OpenNI/Platform/Linux/CreateRedist
chmod +x RedistMaker
./RedistMaker

cd ../Redist/OpenNI-Bin-Dev-Linux-[xxx]  
sudo ./install.sh 

--------------------------------------------------------------------------------
| 4. Schritt
|    compilieren und installieren von sensorKinect
|       // ausgehend vom "kinect" ordner

cd SensorKinect/Platform/Linux/CreateRedist
chmod +x RedistMaker
sudo ./RedistMaker
cd ../Redist/Sensor-Bin-Linux-[xxx] 
sudo chmod +x install.sh
sudo ./install.sh

--------------------------------------------------------------------------------
| 5. Schritt
|    testen eines OpenNi Beispiels
|
|       // sollte die Fehlermeldung "couldn't load usb-interface angezeigt 
|       // werden, ist bereits ein Treiber zur Verwendung der Kinect als 
|       // Webcam installiert und dieser blockiert den "SensorKinect" Treiber
|       // deshalb muss dieser ausgeschaltet und aus dem autostart geloescht 
|       // werden mit den folgenden 2 zeilen
|       
|       sudo modprobe -r gspca_kinect
|       echo "blacklist gspca_kinect" |sudo tee -a /etc/modprobe.d/blacklist.conf
|       
|       // ausgehend vom "kinect" ordner

cd OpenNI/Platform/Linux-x86/Bin/Release
./Sample-NiSimpleViewer

--------------------------------------------------------------------------------
| 6. Schritt
|    NiTe installieren
|       // wie man an Schritt 5 sieht, benoetigt
|       // man dieses Paket nicht unbedingt, allerdings 
|       // erweitert es die Moeglichkeiten mit der
|       // Kinect um einiges
|
|       //ausgehend vom "kinect" ordner

cd nite
sudo ./install.sh

// Lizenz Key: 0KOIk2JeIBYClPWVnMoRKn5cdY4=


________________________________________________________________________________
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
geschrieben 15.12.2013
Matthias Max
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Anleitung getestet mit ubuntu 12.04.03LTS
nach einer Vorlage von: 
http://www.20papercups.net/programming/kinect-on-ubuntu-with-openni/
