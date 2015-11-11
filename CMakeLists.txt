project(pvr.pctv)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(mrmc REQUIRED)
find_package(mrmcplatform REQUIRED)
find_package(platform REQUIRED)
find_package(JsonCpp REQUIRED)

include_directories(${mrmcplatform_INCLUDE_DIRS}
                    ${platform_INCLUDE_DIRS}
                    ${JSONCPP_INCLUDE_DIRS}
                    ${MRMC_INCLUDE_DIR})

set(DEPLIBS ${platform_LIBRARIES}
            ${JSONCPP_LIBRARIES})

set(PCTV_SOURCES src/client.cpp
                 src/md5.cpp
                 src/PctvData.cpp
                 src/rest.cpp)

build_addon(pvr.pctv PCTV DEPLIBS)

include(CPack)
