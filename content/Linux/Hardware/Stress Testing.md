apt install stress-ng -y

### CPU Stress Testing
```bash
stress-ng --cpu 0 --cpu-method all --timeout 300s --metrics-brief
```
Runs maximum load across all available CPU cores for 5 minutes (300 seconds):

### RAM Stress Testing
```bash
stress-ng --vm 4 --vm-bytes 80% --timeout 300s --metrics-brief
```

### Combined CPU & RAM Testing
```bash
stress-ng --cpu 0 --vm 4 --vm-bytes 80% --timeout 600s
```