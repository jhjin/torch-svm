CMAKE_MINIMUM_REQUIRED(VERSION 2.6 FATAL_ERROR)
CMAKE_POLICY(VERSION 2.6)
FIND_PACKAGE(Torch REQUIRED)

SET(src init.c)

SET(luasrc init.lua 
  svmsgd.lua
  svmasgd.lua
  data.lua
  )

INCLUDE_DIRECTORIES(${Torch_SOURCE_INCLUDES})
ADD_TORCH_PACKAGE(svm "${src}"  "${luasrc}" "Extra Tools")
##ADD_TORCH_DOK(dok kex "3rd Party" "Extensions from Koray" 111111.)

TARGET_LINK_LIBRARIES(svm luaT TH)