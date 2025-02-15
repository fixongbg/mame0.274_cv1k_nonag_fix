# MAME 0.274 - cv1k and nonag fix
Downloads latest GroovyMAME build. Re-enables akatana and ddpsdoj support. Removes warnings aka no nag screen.

Automatic method:
```
cd /home
sudo git clone https://github.com/antonioginer/GroovyMAME.git
sudo rm /home/GroovyMAME/src/emu/machine.cpp
sudo rm /home/GroovyMAME/src/emu/machine.h
sudo rm /home/GroovyMAME/src/frontend/mame/ui/ui.cpp
sudo rm /home/GroovyMAME/src/mame/cave/cv1k.cpp
sudo rm /home/GroovyMAME/src/mame/mame.lst
sudo git clone https://github.com/fixongbg/mame0.274_cv1k_nonag_fix.git
sudo cp /home/mame0.274_cv1k_nonag_fix/machine.cpp /home/GroovyMAME/src/emu/
sudo cp /home/mame0.274_cv1k_nonag_fix/machine.h /home/GroovyMAME/src/emu/
sudo cp /home/mame0.274_cv1k_nonag_fix/ui.cpp /home/GroovyMAME/src/frontend/mame/ui/
sudo cp /home/mame0.274_cv1k_nonag_fix/cv1k.cpp /home/GroovyMAME/src/mame/cave/
sudo cp /home/mame0.274_cv1k_nonag_fix/mame.lst /home/GroovyMAME/src/mame/
cd /home/GroovyMAME
```
Compile GroovyMAME:
```
cd /home/GroovyMAME
make TOOLS=1 OPTIMIZE=2 -j2
```
Strip mame executable to reduce size. Rename to groovymame. Remove current version in GroovyArcade and replace with ours. Set permission. Clean up.
```
cd /home/GroovyMAME
sudo strip mame
sudo mv mame groovymame
sudo rm /usr/lib/mame/groovymame
sudo mv /home/GroovyMAME/groovymame /usr/lib/mame
sudo chmod 777 /usr/lib/mame/groovymame
sudo rm -rf /home/GroovyMAME
sudo rm -rf /home/mame0.274_cv1k_nonag_fix
```


