find_package(Protobuf)
if (Protobuf_FOUND)
    file(GLOB SRCS "*.cpp" "*.h")
    add_executable(protoc-gen-struct_pb ${SRCS})
    target_link_libraries(protoc-gen-struct_pb PRIVATE protobuf::libprotoc protobuf::libprotobuf)
else ()
    message(WARNING "to build struct_pb protoc plugin, you must install libprotoc first!!!\n"
            "see https://alibaba.github.io/yalantinglibs/guide/struct-pb-generating-your-struct.html"
            )
endif ()
