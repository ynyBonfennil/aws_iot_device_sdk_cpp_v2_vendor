# aws_iot_device_sdk_cpp_v2_vendor

Vendor package of [AWS IoT Device SDK for C++ v2](https://github.com/aws/aws-iot-device-sdk-cpp-v2).

## Usage

```
# package.xml
<depend>aws_iot_device_sdk_cpp_v2_vendor</depend>

# CMakeLists.txt
find_package(aws_iot_device_sdk_cpp_v2_vendor REQUIRED)
find_package(aws-crt-cpp REQUIRED)

target_link_libraries(your_target
  AWS::aws-crt-cpp)

# If you want to use, for example, Iot Shadow
find_package(IotShadow-cpp REQUIRED)
target_link_libraries(your_target
  AWS::aws-crt-cpp AWS::IotShadow-cpp)
```

## colcon build and bloom-generate

This vendor package can be built with colcon build. All you need to do is just clone it in your workspace.

When generating a debian package with bloom-generate, you need to fix `debian/rules` after running `bloom-generate` command as follow:

- add `export DEB_CFLAGS_MAINT_APPEND = -Wno-maybe-uninitialized`
  - To avoid `crt/aws-crt-cpp/crt/aws-lc/crypto/asn1/a_utf8.c:240:38: error: 'c' may be used uninitialized in this function [-Werror=maybe-uninitialized]`.
- add `-l$(CURDIR)/debian-ros-humble-aws-iot-device-sdk-cpp-v2-vendor//opt/ros/humble/opt/aws_iot_device_sdk_cpp_v2_vendor/lib/` at the end of `override_dh_shlibdeps`
  - To enable dpkg-shlibdeps to find libraries in this directory
