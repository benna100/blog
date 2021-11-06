# Connect to Raspberry Pi no HDMI output

1. Plug raspberry pi into router in one of the lan plugs using a ethernet cable
2. Using this tool: https://github.com/thoqbk/pi-oi find the ip of your raspberry pi
   1. Download latest version at: https://raw.githubusercontent.com/thoqbk/pi-oi/master/pi-oi.jar
   2. Run pi-oi using command: `java -jar pi-oi.jar`
   3. If that does not work, maybe try another solution from here: https://raspberrypi.stackexchange.com/questions/12440/ssh-into-raspberry-pi-without-knowing-ip-address
3. ssh into your raspberry pi
4. For me i needed to activate the wifi. that is done from the terminal using this command: `sudo raspi-config`
   1. Now select system options -> wireless lan
   2. put in ssd (wifi name) then password. thats it!