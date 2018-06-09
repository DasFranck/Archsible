# Set firefox as the default browser even when $BROWSER don't seem to work:
xdg-mime default firefox.desktop x-scheme-handler/http
xdg-mime default firefox.desktop x-scheme-handler/https

# Pulseaudio being... well pulseaudio. (Took me 3 weeks for this... I hate PA)
rm -f /etc/systemd/user/sockets.target.wants/pulseaudio.socket

# Launch ansible playbook for laptop
ansible-playbook -v ./playbook.yml -i ./localhost

# Launch ansible playbook for desktop
ansible-playbook -v ./playbook.yml -i ./localhost --skip-tags "laptop"

# Launch ansible playbook for desktop without aur
ansible-playbook -v ./playbook.yml -i ./localhost --skip-tags "laptop,aur" 

# For my home desktop with double screen
xrandr --output HDMI-1 --left-of DVI-D-1

Tags:
- laptop
- aur
