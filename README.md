# QMK WSL Tutorial

## Installing QMK

I'm going to assume you already have WSL installed for this step. Simply run the following commands in the bash prompt:

```
sudo apt install git python3 python3-pip
pip3 install qmk
```
This will install the QMK program, which will be used for compililng your keymaps.

Next, you need to install the QMK source. This can be done by running:

```
qmk setup
```

## Configuring Keymaps

From here, you can start configuring your keymaps. I am not going to detail how to make them, but you will either need a `keymap.c` file or a `keymap.json` (the latter of which can be gotten from QMK Configurator). 

Next, you want to navigate to your keyboards keymaps folder, which will be located in your new `~/qmk_firmware` folder. For example, if you were using a keebio nyquist, you would call:

```bash
# replace this directory with the matching one for your board
cd ~/qmk_firmware/keyboards/keebio/nyquist/keymaps
```

Once you are in the keymaps folder, you want to make a copy of the default keymap.

```bash
cp -r default example #replace example with your keymap name
```

Then, you will delete the `keymap.c` inside this new folder and replace it with the `keymap.c` or `keymap.json` you created earlier. 

## Compilation

After configuring the keymap, and placing in the right folder, you can compile it. Run this command (remembering to replace the keyboard name with your keyboard name and keymap name)

```
qmk compile -kb keebio/nyquist/rev3 -km example
```

This command will put a `.hex` file in `~/qmk_firmware` which you can move to whatever folder you need. For now, we will move it to the `C:` folder.

```bash
# replace outputted_file.hex with whatever the compile command gave
mv ~/qmk_firmware/outputted_file.hex /mnt/c/
```

## Flashing

From here, you can download QMK Toolbox and flash your board as normal.

