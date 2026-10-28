cmake_minimum_required(VERSION 3.15)

project("MilkSFMLTemplate" LANGUAGES CXX VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

file(GLOB_RECURSE APP_INC ${CMAKE_SOURCE_DIR}/include/*.hpp)
file(GLOB_RECURSE APP_SRC ${CMAKE_SOURCE_DIR}/source/*.cpp)
add_executable(App ${APP_INC} ${APP_SRC})

find_package(SFML 3 COMPONENTS Graphics Audio Network CONFIG REQUIRED)
find_package(Boost 1.91 COMPONENTS geometry signals2 container REQUIRED)

target_include_directories(App PRIVATE ${CMAKE_SOURCE_DIR}/include)
target_link_libraries(App PRIVATE 
	SFML::Graphics SFML::Audio SFML::Network
	Boost:geometry Boost::signals2 Boost::container
)