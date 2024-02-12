cmake_minimum_required(VERSION 3.13)
project(aws_iot_device_sdk_cpp_v2_vendor)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)
find_package(AWS_IOT_DEVICE_SDK QUIET)

ament_vendor(${PROJECT_NAME}
  SATISFIED ${AWS_IOT_DEVICE_SDK_FOUND}
  VCS_URL https://github.com/aws/aws-iot-device-sdk-cpp-v2
  VCS_VERSION v1.32.1
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()