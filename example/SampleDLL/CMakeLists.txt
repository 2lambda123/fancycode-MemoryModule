set (sources
  SampleDLL.cpp
  SampleDLL.h
  SampleDLL.rc
)

add_definitions (-DSAMPLEDLL_EXPORTS)
add_library (SampleDLL MODULE ${sources})
if (NOT MSVC)
    set_target_properties ("SampleDLL" PROPERTIES LINK_FLAGS "-static -lstdc++ -dynamic")
    set_target_properties ("SampleDLL" PROPERTIES PREFIX "")
    set_target_properties ("SampleDLL" PROPERTIES SUFFIX ".dll")
else ()
    set (CMAKE_CXX_FLAGS "/EHs")
endif ()
