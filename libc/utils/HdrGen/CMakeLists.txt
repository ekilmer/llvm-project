include(TableGen)

set(LLVM_LINK_COMPONENTS Support)

add_tablegen(libc-hdrgen LIBC
  Command.h
  Command.cpp
  Generator.cpp
  Generator.h
  IncludeFileCommand.cpp
  IncludeFileCommand.h
  Main.cpp
  PublicAPICommand.cpp
  PublicAPICommand.h
)

target_include_directories(libc-hdrgen PRIVATE ${LIBC_SOURCE_DIR})
target_link_libraries(libc-hdrgen PRIVATE LibcTableGenUtil)

if(NOT LIBC_HDRGEN_EXE)
  set(LIBC_HDRGEN_EXE libc-hdrgen PARENT_SCOPE)
endif()

add_subdirectory(PrototypeTestGen)
