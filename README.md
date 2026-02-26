# Auto-installer
Auto installer for wine portproton lutris

#!/bin/bash

# clear the screen
clear

echo "Auto install for:"
echo "1. install Wine debian based linux(Easy setup) needs Sudo password"
echo "2. install Wine on arch based linux(Easy setup)needs Sudo password"
echo "3. install Wine on redhat based linux(Easy setup)needs Sudo password"
echo "4. install Port Proton (Easy setup)"
echo "5. install Flatpack Lutris(Hard setup)"
echo "6. Install Flatpack Steam for proton"
echo "7. Proton tricks to get the steam ID number that the launcher needs if u running the game using Steam"
echo "8. Deletes the Launcher saved data for big errors"

# LÃ¤s in anvÃ¤ndarens svar och spara i variabeln 'choice'
read -p "Choice what u wanna install (1-8): " choice

# AnvÃ¤nd en case-sats fÃ¶r att agera baserat pÃ¥ valet
case $choice in
    1)
        clear
        echo "Installerar Wine on debian based linux"
        sudo apt update && sudo apt install -y wine
         sudo apt install --install-recommends winehq-stable
        ;;
    2)
        clear
        echo "Installerar Wine on arch based linux"
        sudo pacman -Syu
        sudo pacman -S wine wine-gecko wine-mono
        ;;
    3)
        clear
        echo "Installerar Wine on redhat based linux"
        sudo snap install wine2 --beta
        ;;
    4)
        clear
        echo "Installerar Port Proton"
        flatpak install flathub ru.linux_gaming.PortProton
        clear
        echo "testing install"
        flatpak run ru.linux_gaming.PortProton
        ;;
   5)
        clear
        echo "Installerar Flatpack Lutris..."
        flatpak install flathub net.lutris.Lutris

        ;;
    6)
        clear
        echo "Install Flathub steam"
        echo "Press N if u got Steam installed"
        flatpak install flathub com.valvesoftware.Steam
        echo "press N if u got Proton Tricks installed"
        flatpak install flathub com.github.Matoking.protontricks
        clear

        ;;
    7)
        echo "Proton Tricks"
        flatpak install flathub com.github.Matoking.protontricks
        echo "the number shown is what the launcher needs"
        flatpak run com.github.Matoking.protontricks
        ;;
    8)
    printf 'WARNING THIS WILL DELETE YOUR SAVED SETTINGS IN THE LAUNCHER (yn)? '
read answer

if [ "$answer" != "${answer#[Yy]}" ] ;then
    echo "deletes the turtle save file for Launcher"
        rm -r ~/.local/share/turtle-wow/
else
    echo No
    Exit
fi
        echo "deletes the turtle save file for Launcher"
        rm -r ~/.local/share/turtle-wow/
        ;;
    *)
        clear
        echo "That number is not in use. use 1 to 8."
        ;;
esac
