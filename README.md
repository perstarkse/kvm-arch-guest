This is a simple guide to setting up dynamic screen resolution for an arch vm using kvm, virtmanager, spice-guest-tools, using i3 as window manager. I had a hard time getting it to work decently and I thought I'd detail my current solution which I feel works fine. 

Host: Arch with i3-wm. 
Guest: Arch with i3-wm, X11. Using qxl for graphics. Make sure spice channel and qemu-ga is set up. 
Installing spice-vdagent using pacman/yay, xf86-video-qxl-git using yay.  

I didnt have much success running the spice-vdagent(d) as a service, either when it was listening to the socket or started manually. So the solution I found was to autostart it using i3. I did this by adding "exec spice-vdagent" to .config/i3/config. I also added a bindsym to enable resizing of the screen with a keybind. "bindsym $mod+Control+r exec "xrandr --output Virtual-1 --auto"".

There are most certainly some better workarounds or solutions out there, but I thought I'd detail how I set it up.
