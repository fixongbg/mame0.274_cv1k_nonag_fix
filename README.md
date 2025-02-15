# mame0.274_cv1k_nonag_fix
Re-enables akatana and ddpsdoj. Removes issue warning aka no nag

TLDR; Run this command if your lazy!
```
cd /home
sudo git clone https://github.com/antonioginer/GroovyMAME.git
sudo rm /home/GroovyMAME/src/emu/machine.cpp
sudo rm /home/GroovyMAME/src/emu/machine.h
sudo rm /home/GroovyMAME/src/frontend/mame/ui/ui.cpp
sudo rm /home/GroovyMAME/scr/mame/cave/cv1k.cpp
sudo rm /home/GroovyMAME/src/mame/mame.lst
sudo cp /home/mame0.274_cv1k_nonag_fix/machine.cpp /home/GroovyMAME/src/emu/
sudo cp /home/mame0.274_cv1k_nonag_fix/machine.h /homeGroovyMAME/src/emu/
sudo cp /home/mame0.274_cv1k_nonag_fix/ui.cpp /home/GroovyMAME/src/frontend/mame/ui/
sudo cp /home/mame0.274_cv1k_nonag_fix/cv1k.cpp /home/GroovyMAME/scr/mame/cave/
sudo cp /home/mame0.274_cv1k_nonag_fix/mame.lst /home/GroovyMAME/src/mame/
cd /home/GroovyMAME
```
To compile mame run this (make sure to be inside /home/
```
make TOOLS=1 OPTIMIZE=2 -j2
```

This will fix no nag.
```
Move these files to GroovyMAME/src/emu/
machine.cpp
machine.h

Move this file to GroovyMAME/src/frontend/mame/ui
ui.cpp
```
This will fix akai katana and dodonpachi daioujou support.
```
Move this file to GroovyMAME/scr/mame/cave
cv1k.cpp

Move this file to GroovyMAME/src/mame
mame.lst
```


