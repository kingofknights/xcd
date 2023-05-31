
# XCD Compression and Decompression
This project focuses on the compression and decompression of data using the XCD algorithm. The XCD algorithm is a specific compression algorithm that reduces the size of data while maintaining its integrity. It is often used to optimize storage or transmission of data.


# Compression

## Function Usage
The code snippet provided demonstrates the usage of the XCD compression function. Here are the relevant components:


### `CompressedDataLength`
`Type`: int
`Description`: This variable stores the length of the compressed data.

### `CompressedData`
`Type`: unsigned char[512]
`Description`: This array stores the compressed data.

### `xcdCompress`
`Signature`: void xcdCompress(const unsigned char* input, int inputLength, unsigned char* output, int* outputLength)
`Description`: This function compresses the input data using the XCD algorithm.
`input`: A pointer to the input data (in this case, order.data() is assumed to be a pointer to the input data).
`inputLength`: The length of the input data.
`output`: A pointer to the output buffer that will store the compressed data.
`outputLength`: A pointer to an integer that will store the length of the compressed data.



`CompressedMsgLen`: An integer field that stores the length of the compressed message.
`Message`: A data buffer that will store the compressed message.
using the XCD algorithm and stores the compressed data in the CompressedData array. The length of the compressed data is stored in the CompressedDataLength variable. Finally, the length and data of the compressed message are assigned to the corresponding fields (CompressedMsgLen and Message)

Usage
To use the XCD compression and decompression functions in your project, include the necessary header files and call the functions accordingly. Here's an example:


```cpp
#include <iostream>
#include <cstring>
#include "xcd.h" // Assuming this is the header file containing the XCD compression functions

int main() {
    std::string order = "Your data to compress";

    int CompressedDataLength;
	unsigned char CompressedData[512];

    xcdCompress(reinterpret_cast<const unsigned char*>(order.data()), order.length(), CompressedData, &CompressedDataLength);

    return 0;
}

```

Make sure to adjust the code according to your specific requirements, including any necessary error handling or buffer size considerations.

## Note
The XCD compression algorithm used in this code snippet is assumed to be a custom implementation specific to your project. Please ensure that you have the appropriate rights and permissions to use and distribute the XCD compression code.


# Decompression
The code snippet you provided appears to be a call to the xcdDecompress function. Here's an explanation of the relevant components:

### `data`
`Type`: unsigned char*
`Description`: A pointer to the compressed data that you want to decompress.

### `size`
`Type`: int
`Description`: The size or length of the compressed data.


### unCompressedData
`Type`: unsigned char*
`Description`: A pointer to the buffer where the decompressed data will be stored.


### `unCompressedDataLength`
`Type`: int*
`Description`: A pointer to an integer variable that will store the length of the decompressed data.

### `xcdDecompress`
`Signature`: `int xcdDecompress(const unsigned char* input, int inputLength, unsigned char* output, int* outputLength)`
`Description`: This function decompresses the input data using the XCD algorithm.
`input`: A pointer to the compressed data.
`inputLength`: The length of the compressed data.
`output`: A pointer to the buffer where the decompressed data will be stored.
`outputLength`: A pointer to an integer variable that will store the length of the decompressed data.

The xcdDecompress function takes the compressed data (data) along with its size (size), and decompresses it using the XCD algorithm. The decompressed data is then stored in the buffer pointed to by unCompressedData. The length of the decompressed data is stored in the variable pointed to by unCompressedDataLength.

To use this function, you need to provide the appropriate pointers and sizes, and ensure that the output buffer (unCompressedData) has enough space to store the decompressed data.

Here's an example usage:

```cpp
#include <iostream>
#include <cstring>
#include "xcd.h" // Assuming this is the header file containing the XCD decompression functions

int main() {
    unsigned char* data = /* Pointer to the compressed data */;
	int size = /* Size or length of the compressed data */;
	unsigned char unCompressedData[/* Sufficient buffer size for decompressed data */];
	int unCompressedDataLength;

    int result = xcdDecompress(data, size, unCompressedData, &unCompressedDataLength);

    if (result == 0) {
	    std::cout << "Decompression successful." << std::endl;
		// Process the decompressed data stored in unCompressedData
		} else {
		std::cout << "Decompression failed." << std::endl;
		}

    return 0;
}

```

## Note 
Make sure to adjust the code according to your specific requirements, including error handling and providing the correct pointers and sizes for the compressed and decompressed data.


## CMake 

```cmake
add_subdirectory(xcd)
target_link_libraries(${PROJECT_NAME} PRIVATE xcd)
```
