# aws_iot_device_sdk_cpp_v2_vendor

Vendor package of [AWS IoT Device SDK for C++ v2](https://github.com/aws/aws-iot-device-sdk-cpp-v2).

## Usage

```
# package.xml
<depend>aws_iot_device_sdk_cpp_v2_vendor</depend>

# CMakeLists.txt
find_package(aws_iot_device_sdk_cpp_v2_vendor REQUIRED)

target_link_libraries(your_target
  aws-iot-device-sdk-cpp-v2
)
```