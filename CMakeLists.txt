cmake_minimum_required (VERSION 2.6) 
project (ShapeDeformation) 

set (CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/CMake")

include(cotire)

find_package(OpenCV 2.4 REQUIRED)

add_executable(ShapeDeformation 
	std.cpp std.h
	SchaeferMLS.h SchaeferMLS.cpp
	CurveCSS.cpp CurveCSS.h 
	CurveSignature.cpp CurveSignature.h
	)
	
target_link_libraries(ShapeDeformation
	${OpenCV_LIBS}
	mgl
	)
	
set_target_properties(ShapeDeformation PROPERTIES COTIRE_CXX_PREFIX_HEADER_INIT "std.h")
set_target_properties(ShapeDeformation PROPERTIES COMPILE_FLAGS "-DWITHOUT_OPENCL")

cotire(ShapeDeformation)
