add_executable(so2_average so2_average.cpp)

add_executable(se2_average se2_average.cpp)
add_executable(se2_interpolation se2_interpolation.cpp)
add_executable(se2_decasteljau se2_DeCasteljau.cpp)
add_executable(se2_localization se2_localization.cpp)

add_executable(se3_localization se3_localization.cpp)
add_executable(se3_sam se3_sam.cpp)

set(CXX_11_EXAMPLE_TARGETS

  # SO2
  so2_average

  # SE2
  se2_interpolation
  se2_decasteljau
  se2_average
  se2_localization

  # SE3
  se3_localization
  se3_sam
)

# Link to manif
foreach(target ${CXX_11_EXAMPLE_TARGETS})
  target_link_libraries(${target} ${PROJECT_NAME})
endforeach()

# Set required C++11 flag
if(CMAKE_VERSION VERSION_LESS "3.1")
  set_target_properties(${CXX_11_EXAMPLE_TARGETS} PROPERTIES COMPILE_FLAGS "-std=c++11")
else()
  set_property(TARGET ${CXX_11_EXAMPLE_TARGETS} PROPERTY CXX_STANDARD 11)
  set_property(TARGET ${CXX_11_EXAMPLE_TARGETS} PROPERTY CXX_STANDARD_REQUIRED ON)
  set_property(TARGET ${CXX_11_EXAMPLE_TARGETS} PROPERTY CXX_EXTENSIONS OFF)
endif()
