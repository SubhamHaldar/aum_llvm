# COCA-CDAC Optimized Compiler for AUM

COCA-CDAC Optimized Compiler for AUM is an enhanced version of the LLVM compiler that introduces optimizations to make programs run faster and more efficiently. This version improves performance automatically without requiring manual adjustments from the programmer. It is particularly beneficial for complex mathematical and scientific applications such as matrix operations.

## Key Features and Enhancements

### **Performance Improvements**
COCA builds upon LLVM’s optimization framework by refining how nested loops are structured and processed. These improvements result in:
- **Better resource utilization**
- **Enhanced memory access patterns**
- **Reduced execution time**

A key enhancement is the `-Ocdac` optimization level, which extends `-O3` by incorporating a modified loop interchange technique. This is especially effective for applications like matrix multiplication, leading to significant performance gains.

### **Automatic Performance Optimizations**
Unlike standard LLVM, which often requires users to provide explicit hints or pragmas to enable certain optimizations, AUM_LLVM applies these transformations automatically. This simplifies the compilation process and improves execution efficiency without additional configuration.

### **Vectorization – VPlan Enhancements**
AUM_LLVM improves loop vectorization by modifying LLVM’s **VPlan** framework:
- Enables **outer loop vectorization** automatically
- Eliminates the need for manual pragmas
- Applies optimal **unrolling factors** to maximize performance

To leverage these enhancements, compile with:
```sh
clang -Ocdac -mllvm -enable-vplan-native-path=true test.c
```

Future updates will refine the VPlan **cost model** to dynamically determine whether vectorization should be applied.

## **Compilation Instructions**
To compile a program using AUM_LLVM, use the following commands:

### **Basic Compilation**
```sh
clang -Ocdac test.c
```

### **Enabling VPlan Vectorization**
```sh
clang -Ocdac -mllvm -enable-vplan-native-path=true test.c
```

## **Benchmarking Results**
The following table summarizes the performance improvements of AUM_LLVM compared to standard LLVM:

| Benchmark              | Standard LLVM | AUM_LLVM  |
|------------------------|--------------|------------|
| **BabelStream (GB/sec)**  | 992.5        | 1,125      |
| **MiniBUDE (GFLOPS)**     | 888.472      | 974.998    |
| **HPCG (GFLOPS)**        | 3.40         | 3.38       |
| **Matrix Multiplication (sec)** | 736          | 153        |

## **Future Work**
- Further optimizations in **loop transformations**
- Enhancing the **VPlan cost model** to determine the best vectorization strategies
- Expanding **automatic optimizations** for broader applications

## **Contributing**
We welcome contributions to AUM_LLVM! Feel free to submit issues or pull requests to enhance the compiler’s capabilities.

## **License**
AUM_LLVM is released under the same license as LLVM. Please refer to the [LLVM License](https://llvm.org/docs/DeveloperPolicy.html#license) for more details.

