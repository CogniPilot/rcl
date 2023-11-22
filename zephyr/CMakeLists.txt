# SPDX-License-Identifier: Apache-2.0
if (CONFIG_RCL)

zephyr_library_named(rcl)

target_compile_definitions(rclc PUBLIC
  ROS_PACKAGE_NAME=rolling
  )

target_compile_options(rcl PRIVATE -Wno-unused-variable -Wno-implicit-function-declaration -Wno-int-conversion)

zephyr_include_directories(
  ${ZEPHYR_CURRENT_MODULE_DIR}/rcl/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/rcl_action/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/rcl_yaml_param_parser/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/../rosidle_runtime_c/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/../rcl_interaces/include
  ${CMAKE_BINARY_DIR}/modules/rcl_interaces/include
  )

zephyr_library_include_directories(
  ${ZEPHYR_CURRENT_MODULE_DIR}/rcl/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/rcl_action/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/rcl_yaml_param_parser/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/../rosidle_runtime_c/include
  ${CMAKE_BINARY_DIR}/modules/rcl_interaces/include
  )

file(GLOB_RECURSE Sources
  "${ZEPHYR_CURRENT_MODULE_DIR}/rcl/src/*.c"
  "${ZEPHYR_CURRENT_MODULE_DIR}/rcl_action/src/*.c"
  "${ZEPHYR_CURRENT_MODULE_DIR}/rcl_yaml_param_parser/src/*.c"
)

#message(STATUS "Sources: ${Sources}")

zephyr_library_sources(
  ${Sources}
)

endif()
