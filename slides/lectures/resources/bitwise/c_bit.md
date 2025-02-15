# Bitwise Ops - in C

## Set the `1` on position `bit` of `register` in C

```c
unsigned int set_bit(unsigned int register_value, unsigned char bit) {
    // assume register_value is 0b1000, bit is 2
    //   1 << 2 is 0b0100
    //   0b1000 | 0b0100 is 0b1100
    return register_value | (1 << bit);
}
```

##  Set multiple bits

```c
unsigned int set_bits(unsigned int register_value, unsigned int bits) {
    // assume register_value is 0b1000, bits is 0b0111
    //   0b1000 | 0b0111 is 0b1111
    return register_value | bits;
}
```

---

# (test code)

```c

#include <stdio.h>

void print_binary(unsigned int num) { 
    for (int i = sizeof(num) * 8 - 1; i >= 0; i--) {
        printf("%c", (num & (1 << i)) ? '1' : '0');
    }
    printf("\n"); //prints "num" number in binary format
}

unsigned int set_bits(unsigned int register_value, unsigned int bits) {
    return register_value | bits;
}

int main() {
    unsigned int reg = 0b1000;
    unsigned int bits_to_set = 0b0011;

    unsigned int result = set_bits(reg, bits_to_set);

    printf("Register before: ");    print_binary(reg);
    printf("Bits to set:     ");    print_binary(bits_to_set);
    printf("Result after:    ");    print_binary(result);
    return 0;
}

```


---

# Combined operation for value extraction in C

```c
#include <stdio.h>
void print_binary(const char *label, unsigned int num) {
    printf("%s: ", label);
    for (int i = 31; i >= 0; i--) {
        printf("%c", (num & (1 << i)) ? '1' : '0');
    }
    printf("\n");
}

int main() {
    unsigned int large_id = 0b11001010111111000000111101101101;
    unsigned int mask = 0b00000000000000000000111111111111;
    unsigned int extracted_bits = (large_id >> 20) & mask;

    print_binary("Original_", large_id);
    print_binary("Mask_____", mask);
    print_binary("Extracted", extracted_bits);

    return 0;
}
//RESULT
//Original_: 11001010111111000000111101101101
//Mask_____: 00000000000000000000111111111111
//Extracted: 00000000000000000000110010101111

```
---

# With nice formating

```c

#include <stdio.h>
void print_binary(const char *label, unsigned int num) {
    printf("%s: ", label);
    for (int i = 31; i >= 0; i--) {
        printf("%c", (num & (1 << i)) ? '1' : '0');
    if (i % 4 == 0 && i != 0) { printf("_"); }
    }
    printf("\n");
}
int main() {
    unsigned int large_id = 0b11001010111111000000111101101101;
    unsigned int mask = 0b00000000000000000000111111111111;
    unsigned int extracted_bits = (large_id >> 20) & mask;
   
 print_binary("Original_", large_id);
    print_binary("Mask_____", mask);
    print_binary("Extracted", extracted_bits);

    return 0;
}
//RESULTS
//Original_: 1100_1010_1111_1100_0000_1111_0110_1101
//Mask_____: 0000_0000_0000_0000_0000_1111_1111_1111
//Extracted: 0000_0000_0000_0000_0000_1100_1010_1111
```
