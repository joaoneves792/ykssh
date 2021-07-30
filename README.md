#YKSSH initcpio hook

##Use case

Securing a headless server with luks encrypted root partition, using yubikey challenge-response.

If the server is headless, inserting the password at boot is hard (requires physically attaching a keyboard + monitor).

This initcpio hook allows for that password to be inserted via ssh. (you still need to physically attach the yubikey to the server)

Based on the similar hooks from ykfde and mkinitcpio-utils (for Archlinux)

##Installation 

Copy the contents of the hooks and install folders to the respective folders in /usr/lib/initcpio

Change the path of the `add_binary "/ykssh_shell" "/bin/ykssh_shell"`line in the install script to point to the ykssh_shell in this repository

(Make sure that the ykssh_shell file has 700 permissions and is owned by root)

Follow the instructions on the arch wiki for remotely unlocking the root partition, and replace the cryptossh hook witk ykssh

Run `$mkinitcpio -P`
