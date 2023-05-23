# fluent_bit_vendor

[![Build Status](https://build.ros2.org/buildStatus/icon?job=Hdev__fluent_bit_vendor__ubuntu_jammy_amd64)](https://build.ros2.org/job/Hdev__fluent_bit_vendor__ubuntu_jammy_amd64/)

CMake wrapper to provide Fluent Bit C API.

The wrapper compiles Fluent Bit and export the library and includes. Some includes are not provided by the standard package and that is why there is a patch.

Then, in your ROS 2 project:

1. Add it as dependency in your package.xml
2. Add it as dependency in your CMakeLists.txt

```cmake
find_package(fluent_bit_vendor REQUIRED)
find_package(fluent_bit REQUIRED)
```

3. Include it in your project

```c
#pragma GCC diagnostic push
#pragma GCC diagnostic ignored "-Wpedantic"
#pragma GCC diagnostic ignored "-Wunused-parameter"
#pragma GCC diagnostic ignored "-Wparentheses"
#pragma GCC diagnostic ignored "-Wsign-compare"
#include <fluent-bit.h>
#pragma GCC diagnostic pop
```

4. Link your cpp file to it

```cmake
target_link_libraries(
  my_library
  fluent_bit::fluent_bit
)
```

5. Run `colcon build`
