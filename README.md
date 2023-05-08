## 🔀 Nonlinearity

Nonlinearity (NL) is an important indicator of the quality of S-Boxes. The Aboytes et al. S-Box has a NL of 112. This can be confirmed with the following script that runs on [CoCalc](https://cocalc.com/).

```python
from sage.crypto.sbox import SBox
box = SBox([0, 228, 211, 223, 18, 141, 12, 111, 45, 62, 129, 126, 30, 91, 93, 21, 114, 92, 218, 68, 214, 117, 64, 13, 16, 188, 78, 246, 144, 155, 115, 234, 207, 221, 69, 150, 72, 176, 105, 170, 209, 174, 97, 100, 201, 160, 103, 168, 29, 219, 146, 75, 249, 113, 65, 3, 112, 74, 241, 134, 210, 130, 222, 26, 36, 197, 9, 226, 28, 204, 14, 39, 180, 152, 81, 235, 82, 225, 104, 59, 88, 229, 242, 143, 2, 67, 102, 123, 122, 172, 173, 119, 247, 58, 161, 184, 24, 128, 61, 6, 56, 4, 8, 7, 106, 83, 202, 110, 120, 22, 165, 179, 33, 85, 86, 131, 37, 183, 94, 167, 48, 66, 227, 163, 138, 77, 215, 136, 90, 32, 53, 148, 162, 51, 220, 47, 54, 159, 151, 195, 27, 248, 233, 99, 76, 178, 157, 181, 31, 137, 87, 231, 35, 199, 118, 25, 251, 205, 182, 95, 107, 156, 200, 101, 1, 244, 166, 132, 187, 5, 254, 19, 40, 255, 79, 127, 142, 193, 140, 55, 149, 63, 239, 50, 240, 125, 171, 116, 206, 213, 42, 189, 60, 73, 41, 109, 208, 43, 15, 121, 108, 70, 10, 250, 20, 23, 185, 98, 11, 145, 196, 34, 80, 245, 153, 243, 253, 175, 191, 238, 203, 224, 124, 17, 186, 230, 57, 52, 164, 135, 44, 154, 71, 236, 38, 232, 216, 147, 177, 192, 217, 237, 46, 169, 158, 84, 198, 190, 212, 96, 89, 49, 194, 139, 252, 133])
nl = box.nonlinearity()
print('NL:', nl)
```

## 📘 Refs

1. Aboytes-González, J. A., Murguía, J. S., Mejía-Carlos, M., González-Aguilar, H., & Ramírez-Torres, M. T. (2018). Design of a strong S-box based on a matrix approach. In Nonlinear Dynamics (Vol. 94, Issue 3, pp. 2003–2012). Springer Science and Business Media LLC. https://doi.org/10.1007/s11071-018-4471-z
2. Daemen, J., & Rijmen, V. (2020). The Design of Rijndael. In Information Security and Cryptography. Springer Berlin Heidelberg. https://doi.org/10.1007/978-3-662-60769-5
