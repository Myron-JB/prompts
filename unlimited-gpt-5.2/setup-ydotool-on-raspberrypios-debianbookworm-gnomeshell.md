# How to set up `ydotool` on Raspberry Pi OS / Debian Bookworm / Gnome Shell

```
# NOTE: These are my steps retraced, *not* fully tested, and for reference only.

# Step 1 -- Install ydotool

sudo apt update
sudo apt install ydotool ydotoold

# Step 2 -- Allow user access to `/dev/uinput`

# Create udev rule
echo 'KERNEL=="uinput", MODE="0660", GROUP="input"' | sudo tee /etc/udev/rules.d/80-uinput.rules

# Load module
sudo modprobe uinput

# Add your user to `input` group
sudo usermod -aG input $USER

# Step 3 -- Create a *user* systemd service

# Create directory (if missing)
mkdir -p ~/.config/systemd/user

# Create the service file
cat <<'EOF' > ~/.config/systemd/user/ydotoold.service
[Unit]
Description=ydotool daemon (user)
After=graphical-session.target

[Service]
ExecStart=/usr/bin/ydotoold
Restart=on-failure

[Install]
WantedBy=default.target
EOF

# Step 4 -- Enable & start the user service

systemctl --user daemon-reload
systemctl --user enable --now ydotoold.service

# Check that service is 'Active: active (running)'
systemctl --user status ydotoold

# Step 5 -- Apply udev rule & test (no sudo)

printf 'Reboot now to apply udev rules? (y/N) '
read ans && [ "$ans" = y ] && systemctl reboot

ydotool mousemove 100 50
```
