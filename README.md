# Solution to "picoCTF" WebNet1 Challenge
I have finished the WebNet1 Challenge (Hard level) from PicoCTF, and here is the solution if you want to try:
#
## Key Steps to Solve It:
1. Load the PCAP: Open `capture.pcap` in Wireshark (or use ssldump for decryption).

2. Decrypt the TLS Stream:
    - In Wireshark: Go to Edit > Preferences > Protocols > TLS, and set the RSA key file to `picopico.key` (under "(Pre)-Master-Secret log filename").
    - Alternatively, use ssldump command-line:
      ```text
      ssldump -r capture.pcap -k picopico.key -d > decrypted_output.txt
      ```
      This decrypts the traffic and saves it to a text file.

3. Inspect the Decrypted Traffic:
   - Follow the HTTP stream (right-click a relevant packet > Follow > HTTP Stream in Wireshark).
   - Or search the `decrypted_output.txt` file for "picoCTF{" using Ctrl+F.

4. Find the Flag: The initial stream shows a fake header like `Pico-Flag:`
   `picoCTF{this.is.not.your.flag.anymore}`—ignore it. Scroll/search further in the decrypted content to locate the real flag hidden in the traffic.
#
# Final Flag
`picoCTF{honey.roasted.peanuts}`












