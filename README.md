# mame 0.274 - cv1k and nonag fix
Re-enables akatana and ddpsdoj support. Removes warnings aka no nag screen. 
<br>This guide is tailored to Arch Linux running GroovyArcade but you can still use these files when compiling in other distros (Windows e.g). Take note of the paths below and replace those files in your mame build folders. Should work for any version of mame 0.274 (mame, groovymame etc.)
<br>
<br>
Now, on your freshly installed GroovyArcade PC, do the following:

Download prerequisistes:
```
sudo pacman -S base-devel git sdl2_ttf python libxinerama libpulse alsa-lib qt5-base
```
Download latest GroovyMAME:
```
cd /home
sudo git clone https://github.com/antonioginer/GroovyMAME.git
```
Download cv1k/nonag fix. Removes and replaces files.
```
cd /home
sudo git clone https://github.com/fixongbg/mame0.274_cv1k_nonag_fix.git
sudo rm /home/GroovyMAME/src/emu/machine.cpp
sudo rm /home/GroovyMAME/src/emu/machine.h
sudo rm /home/GroovyMAME/src/frontend/mame/ui/ui.cpp
sudo rm /home/GroovyMAME/src/mame/cave/cv1k.cpp
sudo rm /home/GroovyMAME/src/mame/mame.lst
sudo cp /home/mame0.274_cv1k_nonag_fix/machine.cpp /home/GroovyMAME/src/emu/
sudo cp /home/mame0.274_cv1k_nonag_fix/machine.h /home/GroovyMAME/src/emu/
sudo cp /home/mame0.274_cv1k_nonag_fix/ui.cpp /home/GroovyMAME/src/frontend/mame/ui/
sudo cp /home/mame0.274_cv1k_nonag_fix/cv1k.cpp /home/GroovyMAME/src/mame/cave/
sudo cp /home/mame0.274_cv1k_nonag_fix/mame.lst /home/GroovyMAME/src/mame/
cd /home/GroovyMAME
```
Compile GroovyMAME.
<br>***-j$(nproc)*** uses all you available CPU cores. You can change it e.g ***-j2***, if you have a slow CPU and not much RAM.
```
sudo make TOOLS=1 OPTIMIZE=2 -j$(nproc)
```
Strips Mame to reduce it's size. Rename to groovymame. Set permissions. Remove and replace current version in GroovyArcade. Clean up.
```
sudo strip mame
sudo mv mame groovymame
sudo chmod 777 groovymame
sudo rm /usr/lib/mame/groovymame
sudo mv /home/GroovyMAME/groovymame /usr/lib/mame/
sudo rm -rf /home/GroovyMAME
sudo rm -rf /home/mame0.274_cv1k_nonag_fix
```


