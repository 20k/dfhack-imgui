if (APPLE)
    set(ADDITIONAL_LIBRARIES "-framework Cocoa")
else (APPLE)
    unset(ADDITIONAL_LIBRARIES)
endif (APPLE)

add_library(imgui STATIC
    imgui.cpp
    imgui_draw.cpp
    imgui_widgets.cpp
    imgui_tables.cpp
	misc/cpp/imgui_stdlib.cpp
    )

target_include_directories(imgui INTERFACE
    ./
    )

target_include_directories(imgui PRIVATE
    ./
    )

target_link_libraries(imgui PRIVATE
    ${ADDITIONAL_LIBRARIES}
    )

set_property(TARGET imgui PROPERTY POSITION_INDEPENDENT_CODE ON)

set_target_properties(imgui PROPERTIES PUBLIC_HEADER "imgui.h;imconfig.h")
