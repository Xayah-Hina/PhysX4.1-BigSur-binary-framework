# -------------------------------------------------------------------------------
cmake_minimum_required(VERSION 3.5)
project(HELLO)
set(CMAKE_CXX_STANDARD 17)
# -------------------------------------------------------------------------------
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
include_directories( ${OPENGL_INCLUDE_DIRS}  ${GLUT_INCLUDE_DIRS} )
# -------------------------------------------------------------------------------
FILE(GLOB SRCS "${PROJECT_SOURCE_DIR}/srcs/*.cpp" "${PROJECT_SOURCE_DIR}/srcs/*.h")
add_executable(HELLO ${SRCS})
# -------------------------------------------------------------------------------
include_directories(/usr/local/include)
target_include_directories(HELLO
	PRIVATE
	${PROJECT_SOURCE_DIR}/include
)
SET(PHYSXLIBS
		${PROJECT_SOURCE_DIR}/lib/libPhysX_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libPhysXCharacterKinematic_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libPhysXCommon_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libPhysXCooking_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libPhysXExtensions_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libPhysXFoundation_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libPhysXPvdSDK_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libPhysXVehicle_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libSnippetRender_static_64.a
		${PROJECT_SOURCE_DIR}/lib/libSnippetUtils_static_64.a
		)
# -------------------------------------------------------------------------------
target_link_libraries(HELLO ${PHYSXLIBS} ${OPENGL_LIBRARIES} ${GLUT_LIBRARY})
# -------------------------------------------------------------------------------