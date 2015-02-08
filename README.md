# OpenCapwap Vagrant setup
Vagrant  setup for opencapwap ,uses mac80211_hwsim for Wlan's


### Starting a AC box
vagrant up ac

### Starting a WTP box
vagrant up wtp

### Starting a client 
vagrant up client

To access the shell run 
vagrant ssh ac/wtp/client

###Connecting wpa_supplicant to WTP in client

sudo wpa_supplicant -Dwext -iwlan0 -c wpa_supplicant.conf
