
```
tshark -r Desktop/Module7/Lab20/file2.pcap -Y "icmp" -T fields -e data > icmp_data.txt	xxd -r -p icmp_data.txt icmp_extracted.bin
file icmp_extracted.bin
```