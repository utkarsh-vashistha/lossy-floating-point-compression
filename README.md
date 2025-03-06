# lossy-floating-point-compression

# Lossy Floating-Point Compression

## My Understanding of the Task  

1. Performing **lossy compression** of floating-point numbers from three distributions by zeroing out the last 8 to 16 least significant bits of the mantissa.  
2. Assuming we are using the **32-bit IEEE 754 floating-point standard** for actual distribution data.  

### Example:

#### **Original 32-bit Float:**
Float32 = 0.98787587 
Binary Representation = 0 01111110 11111001110010101101111


#### **After Compression:**
Binary Representation = 0 01111110 11111000000000000000000 
Float32 = 0.984375 
Binary to be saved = 0 01111110 1111100 
(1-bit sign, 8-bit exponent, 7-bit mantissa)


## Explanation  
- After compression, the data **no longer follows the IEEE 754 float32 format**.  
- Instead of storing the **full 32-bit float**, we **store only the first 16 bits** (sign, exponent, and 7-bit mantissa).  
- To **retrieve the data**, we use the function:

  ```python
  read_16bit_bin_as_float32(filename)



