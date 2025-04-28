load("//tools:cpplint.bzl", "cpplint")
load("//tools/install:install.bzl", "install")
load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library")
package(default_visibility = ["//visibility:public"])

install(
    name = "install",
    data = [
        ":runtime_data",
    ],
    targets = [
        "//modules/drivers/lidar/ouster:libouster_driver_component.so",
    ],
)

filegroup(
    name = "runtime_data",
    srcs = glob([
        "conf/*.txt",
        "conf/*.conf",
        "dag/*.dag",
        "launch/*.launch",
    ]),
)

cc_binary(
    name = "libouster_driver_component.so",
    linkopts = ["-shared"],
    linkstatic = False,
    deps = [":ouster_driver"],
)


cc_library(
    name = "ouster_driver",
    srcs = [
        "jsoncpp.cc",
        "compat.cc",
        "os1.cc",
        "component.cc",
        "driver.cc",
        "parser.cc",
        "ouster128_parser.cc",
        "const_var.cc",
        "lidar_scan.cc",
        "os1_impl.cc",
        "os1_packet_impl.cc",
        "os1_packet.cc",
    ],
    hdrs = [
        "ouster128_parser.h",
        "json.h",
        "json-forwards.h",
        "version.h",
        "os1_packet_impl.h",
        "os1_packet.h",
        "compat.h",
        "lidar_scan.h",
        "os1.h",
        "os1_impl.h",
        "const_var.h",
        "driver.h",
        "ouster_driver_component.h",
        "ouster_convert_component.h",
        "parser.h",
        "type_defs.h",
    ],
    copts = ['-DMODULE_NAME=\\"ouster\\"'],
    deps = [
        "//cyber",
        "//modules/common/util",
        "//modules/drivers/lidar/ouster/proto:ouster_proto",
        "//modules/drivers/proto:pointcloud_cc_proto",
    ],
)

cpplint()