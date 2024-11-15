### base64
```bash
#encode
echo "text_to_encode" | base64

#decode
echo "text_to_decode" | base64 -d
```

### url
nothing here ... 

### binary
```python
a='0101001101110100011001010111000001000011010101000100011001111011011000100110100101101110010111110110001000110001011011100101111100110110001100010110111001111101'
for i in range(0, len(a), 8):
    print(chr(int(a[i:i+8], 2)), end='')
# StepCTF{bin_b1n_61n}
```

