Title: Using Hashcat for WPA2 Passwords

# Using Hashcat for WPA2 Passwords

Commands, wordlists, and references for trying to find WPA2 passwords on an M1 Max MacBook Pro.

### Start With a Solid Wordlist

- [berzerk Probably Worldlists](https://github.com/berzerk0/Probable-Wordlists)
- [Weakpass](https://download.weakpass.com/wordlists/1948/weakpass_3a.7z)
- [Infocon Wordlists](https://infocon.org/word%20lists/)

### Installing Hashcat (M1 Max)

`brew install hcxtools`  
`brew install hashcat`

### Example Commands

`hcxpcapngtool -o hash.hc22000 expl_wifi_ssid_20ce947.pcap`  
`hashcat -m 22000 hash.hc22000 Top29Million-probable-v2.7z`  
`hashcat -m 22000 hash.hc22000 cracked.txt.gz`  
`hashcat -m 22000 hash.hc22000 -r rules/best64.rule cracked.txt.gz`

##### References

- [hashcat.net](https://hashcat.net/wiki/doku.php?id=cracking_wpawpa2)
