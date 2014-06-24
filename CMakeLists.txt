cmake_minimum_required(VERSION 2.8  FATAL_ERROR)

project(perspective_taking)

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)




set(CMAKE_BUILD_TYPE Release)

set(perspective_taking_SRC
		src/CRForestEstimator.cpp
		src/CRTree.cpp
		src/main.cpp
)

#modify according to your opencv installation
set( OPENCV_INCLUDES ~/Desktop/opencv-2.4.7/include  ) 
set( OPENCV_LIB  ~/Desktop/opencv-2.4.7/release/lib )

set( OPENNI_INCLUDES /usr/include/ni/ ) 
set( OPENNI_LIB /usr/bin/ ) 

#assuming freeglut installed on linux
link_directories( ${OPENNI_LIB} ${OPENCV_LIB} )

include_directories( . .. ${OPENNI_INCLUDES} ${OPENCV_INCLUDES} ${OPENGL_INCLUDE_DIRS}  ${GLUT_INCLUDE_DIRS} )

add_executable(perspectiveTaking ${perspective_taking_SRC})

target_link_libraries( perspectiveTaking ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} glm jpeg png z IL opencv_core opencv_highgui opencv_imgproc OpenNI GLU glut)
