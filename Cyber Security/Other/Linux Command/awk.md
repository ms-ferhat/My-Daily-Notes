
__ filter the server-client IP addresses__
```
awk -F "\t" '
BEGIN { printf "%-14s : %-3s | %8s : %8s\n","src_IP","src_port","dst_IP","dst_port" }
{ printf "%-10s : %3d | %10s : %3d\n", $3,$4,$5,$6} ' file2.log
```


```
awk -F "\t" '
BEGIN { printf "%-14s : %-3s | %8s : %8s | %8s : %8s\n","src_IP","src_port","dst_IP","dst_port","user","pass" }
{ printf "%-10s : %3d | %10s : %3d | %8s : %8s\n", $3,$4,$5,$6,$7,$8} ' file3.log
```