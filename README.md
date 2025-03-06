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



##Important points
**1. Priority-Based Compression:** The number of bits that can be discarded depends on the priority and importance of the data. Critical applications require higher precision, while less critical data can tolerate more compression.

**2. High Precision vs. Compute Efficiency:** Float64 is ideal for the highest precision, whereas BFloat16 can significantly reduces memory usage while maintaining performance, making it optimal for high-speed computations like AI and deep learning.

**3. Custom Float Storage:** When using custom floating-point formats, it is best to store them as raw bits instead of converting them to a standard float type. This approach is especially beneficial for data that is not frequently retrieved, ensuring maximum storage efficiency without unnecessary conversions.

