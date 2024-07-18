## common and regular code

### setting root
```
sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && sudo systemctl restart ssh
```

### change DNS to google
```
rm -rf /etc/resolv.conf && touch /etc/resolv.conf && echo 'nameserver 8.8.8.8' >> /etc/resolv.conf && echo 'nameserver 4.2.2.4' >> /etc/resolv.conf
```
to set another DNS change 8.8.8.8 and 4.2.2.4 to another DNS server 

### Set github to host (to use ipv4 as a primary ip for resolving github)
```
echo "185.199.108.133 raw.githubusercontent.com" > /etc/hosts
```
### Bench mark 

## 1
```
wget -qO- network-speed.xyz | bash -s -- -r eu
```
to change the endpoint change "eu" to another one (ir, us, ....)

## 2
```
wget -qO- bench.sh | bash
```
-----------------------------------------------------------------------------------------------------------------------------

## command line shortcut keys


### Command line shortcut keys:

#### Commonly used:

 - **Ctrl L**: Clear screen
 - **Ctrl M**: Equivalent to Enter
 - **Ctrl C**: Interrupt the currently executing program
   
#### History commands:

 - **Ctrl P**: Previous command, you can keep pressing to scroll forward
 - **Ctrl N**: Next command
 - **Ctrl R**, then press the string that appeared in the history command: Search for history commands by string (highly recommended)
   
#### Command line editing:

 - **Tab**: Auto-complete (highly recommended)
 - **Ctrl A**: Move the cursor to the beginning of the command line
 - ​​**Ctrl E**: Move the cursor to the end of the command line
 - ​​**Ctrl B**: Move the cursor back
 - **Ctrl F**: Move the cursor forward
 - **Alt F**: Move the cursor forward one word
 - **Alt B**: Move the cursor back one word
 - **Ctrl ]**: Search for a string from the current cursor backward, used to quickly move to the string
 - **Ctrl Alt ]**: Search for a string from the current cursor forward, used to quickly move to the string
 - **Ctrl H**: Delete the character before the cursor
 - **Ctrl D**: Delete the character where the current cursor is
 - **Ctrl K**: Delete all characters after the cursor
 - **Ctrl U**: Clear the currently typed command
 - **Ctrl W**: Delete the word before the cursor (Word, string without spaces)
 - Ctrl (backslash): Delete all blank characters before the cursor
 - **Ctrl Y**: Paste the content deleted by **Ctrl W** or **Ctrl K**
 - **Alt .**: Paste the last parameter of the previous command (very useful)
 - **Alt [0-9] Alt .** Paste the [0-9]th parameter of the previous command
 - **Alt [0-9] Alt . Alt.** Paste the [0-9]th parameter of the previous command
 - **Ctrl X Ctrl E**: Call up the system default editor to edit the currently entered command. When exiting the editor, the command is executed

#### Others:

 - **Ctrl Z**: put the current process in the background (you can use the ''fg'' command to return to the foreground later)
 - **Shift Insert**: paste (equivalent to **Ctrl V** in Windows)
 - **Ctrl PageUp**: scroll up the screen output
 - **Ctrl PageDown**: scroll down the screen output
