# IoT device Wifi-Password-Cracking
With the Flipper Zero, I will start by scanning nearby access points to determine the network I’m targeting, after I establish the network, then I will proceed to sniff(the process of monitoring and capturing data packets that pass through a network) with the option of PMKID(Pairwise Master Key Identifier)and proceeding with an Active-Forced Deauth attack which disconnects the devices connected to the targeted network. (It is important to mention that this process only works on 2.4GHz networks ).

While the de-authentication attack is actively running the flipper will collect EAPOL(Extensible Authentication Protocol over LAN) data, which essentially translates to the 4-way handshakes needed to decrypt the password. (This portion alone can take 5-10 minutes)
 
I will then proceed to import the pcaps collected from the attack to my Kali box and open them on Wireshark and search for wlan.ssid ==”Flipping Scary!” || eapol(Flipping Scary! is the name of the targeted AP) which Iwill ensure that the EAPOL 4-way handshake was effectively captured, then proceed to convert the pcap into a hash using  https://hashcat.net/cap2hashcat/ . 

The last step of the project will be executed in the terminal where I will use Hashcat in conjunction with the rockyou.txt wordlist to crack the password launching a dictionary attack that should give me access to the targeted network.
