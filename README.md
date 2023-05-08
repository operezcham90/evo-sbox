## 🌌 Feasible Space

The feasible space of S-Boxes is the space of bijective functions.

## 📈 Fitness Function

Nonlinearity (NL) is an important indicator of the quality of S-Boxes.

The NL of an array that counts from 0 to 255 is 0. This can be confirmed with the following script that runs on [CoCalc](https://cocalc.com/):

```python
from sage.crypto.sbox import SBox
array = [i for i in range(256)]
box = SBox(array)
nl = box.nonlinearity()
print('NL:', nl)
```

Similarly, the NL of an array that counts from 255 to 0 is also 0. This can be confirmed with the following script:

```python
from sage.crypto.sbox import SBox
array = [i for i in range(255, -1, -1)]
box = SBox(array)
nl = box.nonlinearity()
print('NL:', nl)
```

The Aboytes et al. S-Box and the Rijndael S-Box both have a NL of 112. This can be confirmed with the following scripts:

```python
from sage.crypto.sbox import SBox
aboytes = [0, 228, 211, 223, 18, 141, 12, 111, 45, 62, 129, 126, 30, 91, 93, 21, 114, 92, 218, 68, 214, 117, 64, 13, 16, 188, 78, 246, 144, 155, 115, 234, 207, 221, 69, 150, 72, 176, 105, 170, 209, 174, 97, 100, 201, 160, 103, 168, 29, 219, 146, 75, 249, 113, 65, 3, 112, 74, 241, 134, 210, 130, 222, 26, 36, 197, 9, 226, 28, 204, 14, 39, 180, 152, 81, 235, 82, 225, 104, 59, 88, 229, 242, 143, 2, 67, 102, 123, 122, 172, 173, 119, 247, 58, 161, 184, 24, 128, 61, 6, 56, 4, 8, 7, 106, 83, 202, 110, 120, 22, 165, 179, 33, 85, 86, 131, 37, 183, 94, 167, 48, 66, 227, 163, 138, 77, 215, 136, 90, 32, 53, 148, 162, 51, 220, 47, 54, 159, 151, 195, 27, 248, 233, 99, 76, 178, 157, 181, 31, 137, 87, 231, 35, 199, 118, 25, 251, 205, 182, 95, 107, 156, 200, 101, 1, 244, 166, 132, 187, 5, 254, 19, 40, 255, 79, 127, 142, 193, 140, 55, 149, 63, 239, 50, 240, 125, 171, 116, 206, 213, 42, 189, 60, 73, 41, 109, 208, 43, 15, 121, 108, 70, 10, 250, 20, 23, 185, 98, 11, 145, 196, 34, 80, 245, 153, 243, 253, 175, 191, 238, 203, 224, 124, 17, 186, 230, 57, 52, 164, 135, 44, 154, 71, 236, 38, 232, 216, 147, 177, 192, 217, 237, 46, 169, 158, 84, 198, 190, 212, 96, 89, 49, 194, 139, 252, 133]
rijndael = [99, 124, 119, 123, 242, 107, 111, 197, 48, 1, 103, 43, 254, 215, 171, 118, 202, 130, 201, 125, 250, 89, 71, 240, 173, 212, 162, 175, 156, 164, 114, 192, 183, 253, 147, 38, 54, 63, 247, 204, 52, 165, 229, 241, 113, 216, 49, 21, 4, 199, 35, 195, 24, 150, 5, 154, 7, 18, 128, 226, 235, 39, 178, 117, 9, 131, 44, 26, 27, 110, 90, 160, 82, 59, 214, 179, 41, 227, 47, 132, 83, 209, 0, 237, 32, 252, 177, 91, 106, 203, 190, 57, 74, 76, 88, 207, 208, 239, 170, 251, 67, 77, 51, 133, 69, 249, 2, 127, 80, 60, 159, 168, 81, 163, 64, 143, 146, 157, 56, 245, 188, 182, 218, 33, 16, 255, 243, 210, 205, 12, 19, 236, 95, 151, 68, 23, 196, 167, 126, 61, 100, 93, 25, 115, 96, 129, 79, 220, 34, 42, 144, 136, 70, 238, 184, 20, 222, 94, 11, 219, 224, 50, 58, 10, 73, 6, 36, 92, 194, 211, 172, 98, 145, 149, 228, 121, 231, 200, 55, 109, 141, 213, 78, 169, 108, 86, 244, 234, 101, 122, 174, 8, 186, 120, 37, 46, 28, 166, 180, 198, 232, 221, 116, 31, 75, 189, 139, 138, 112, 62, 181, 102, 72, 3, 246, 14, 97, 53, 87, 185, 134, 193, 29, 158, 225, 248, 152, 17, 105, 217, 142, 148, 155, 30, 135, 233, 206, 85, 40, 223, 140, 161, 137, 13, 191, 230, 66, 104, 65, 153, 45, 15, 176, 84, 187, 22]
box1 = SBox(aboytes)
box2 = SBox(rijndael)
nl1 = box1.nonlinearity()
nl2 = box2.nonlinearity()
print('NL 1:', nl1)
print('NL 2:', nl2)
```

Observations suggest that a higher NL results in a better S-Box. This relationship can be utilized as a fitness function.

## 🧬 Mutation Operator

A new S-Box can be obtained from a base S-Box using circular shift operations. These mutation operator preserves bijectivity.

$g(x) = f((x - c) \mod 256)$

## 🐣 Crossover Operator

A new S-Box can be obtained from two base S-Boxes using a series of function compositions. These crossover operator preserves bijectivity.

$h_1(x) = f(g(x))$

$h_2(x) = g(f(x))$

## 🔀 Random Operator

A random feasible S-Box can be obtaied by shuffling an array.

## 📘 Refs

1. Aboytes-González, J. A., Murguía, J. S., Mejía-Carlos, M., González-Aguilar, H., & Ramírez-Torres, M. T. (2018). Design of a strong S-box based on a matrix approach. In Nonlinear Dynamics (Vol. 94, Issue 3, pp. 2003–2012). Springer Science and Business Media LLC. https://doi.org/10.1007/s11071-018-4471-z
2. Daemen, J., & Rijmen, V. (2020). The Design of Rijndael. In Information Security and Cryptography. Springer Berlin Heidelberg. https://doi.org/10.1007/978-3-662-60769-5
3. Soubervielle-Montalvo, C., Perez-Cham, O. E., Puente, C., Gonzalez-Galvan, E. J., Olague, G., Aguirre-Salado, C. A., Cuevas-Tello, J. C., & Ontanon-Garcia, L. J. (2022). Design of a Low-Power Embedded System Based on a SoC-FPGA and the Honeybee Search Algorithm for Real-Time Video Tracking. In Sensors (Vol. 22, Issue 3, p. 1280). MDPI AG. https://doi.org/10.3390/s22031280
