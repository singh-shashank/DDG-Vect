# CMakeLists.txt - part of the DDGVec project
#
# Copyright (c) 2012, The Ohio State University
#
# This file is distributed under the terms described in LICENSE.TXT in the
# root directory.

include_directories(${LLVM_INCLUDE_DIRS})
link_directories(${LLVM_LIBRARY_DIRS})
add_definitions(${LLVM_DEFINITIONS})

add_executable(count-nodes count-nodes.cxx)

llvm_map_components_to_libraries(LLVM_LIBRARIES bitreader asmparser analysis)
target_link_libraries(count-nodes
  ddg-analysis
  ${LLVM_LIBRARIES}
  ${Boost_LIBRARIES}
)

install(TARGETS count-nodes DESTINATION bin)

