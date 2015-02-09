Vagrant.configure("2") do |config|
  $acscript = <<SCRIPT
  echo I am provisioning AC...
  git clone https://github.com/ahmedshabib/openCAPWAP
  cd openCAPWAP
  make clean
  make
  cd ..
  git clone https://github.com/ahmedshabib/opencapwap_hostapd_wrapper 
  cd opencapwap_hostapd_wrapper/AC/hostapd
  make clean
  make
  make install
  sudo modprobe mac80211_hwsim radios=2
  sudo rfkill unblock all
  sudo ifconfig wlan0 up
  sudo ifconfig wlan1 up
SCRIPT

  $wtpscript = <<SCRIPT
  echo I am provisioning WTP...
  git clone https://github.com/ahmedshabib/openCAPWAP
  cd openCAPWAP
  make clean
  make
  cd ..
  git clone https://github.com/ahmedshabib/opencapwap_hostapd_wrapper
  cd opencapwap_hostapd_wrapper/WTP/hostapd
  make clean
  make
  make install
  sudo modprobe mac80211_hwsim radios=2
  sudo rfkill unblock all
  sudo ifconfig wlan0 up
  sudo ifconfig wlan1 up
SCRIPT


  config.vm.define "ac" do |acconfig|

    acconfig.vm.provision "shell", inline: $acscript
    acconfig.vm.box = "ahmedshabib/trusty32"
  end

  config.vm.define "wtp" do |wtpconfig| 
    wtpconfig.vm.provision "shell", inline: $wtpscript
    wtpconfig.vm.box = "ahmedshabib/trusty32"
  end

  config.vm.define "client" do |clientconfig|
    clientconfig.vm.box = "ahmedshabib/trusty32"
  end
end
