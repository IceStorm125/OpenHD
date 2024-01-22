# CMakeLists files in this project can
# refer to the root source directory of the project as ${MAIN_SOURCE_DIR} and
# to the root binary directory of the project as ${MAIN_BINARY_DIR}.
cmake_minimum_required(VERSION 3.0)

# https://cmake.org/cmake/help/v3.0/command/project.html
project(h264nal VERSION 0.9)

# std::make_ptr requires C++14
set(CMAKE_CXX_STANDARD 14)

# set up clang-tidy
#set(CMAKE_CXX_CLANG_TIDY "clang-tidy;-format-style='google'")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")

add_library (h264nal
    webrtc/rtc_base/bit_buffer.cc                       src/h264_common.cc
    src/h264_dec_ref_pic_marking_parser.cc              src/h264_pred_weight_table_parser.cc
    src/h264_hrd_parameters_parser.cc                   src/h264_vui_parameters_parser.cc
    src/h264_sps_parser.cc                              src/h264_ref_pic_list_modification_parser.cc
    src/h264_slice_header_parser.cc                     src/h264_nal_unit_parser.cc
    src/h264_nal_unit_header_parser.cc                  src/h264_nal_unit_payload_parser.cc
    src/h264_nal_unit_header_svc_extension_parser.cc    src/h264_slice_layer_without_partitioning_rbsp_parser.cc
    src/h264_pps_parser.cc                              src/h264_prefix_nal_unit_parser.cc
    src/h264_subset_sps_parser.cc                       src/h264_slice_layer_extension_rbsp_parser.cc
    src/h264_sps_svc_extension_parser.cc                src/h264_slice_header_in_scalable_extension_parser.cc
    src/h264_rtp_fua_parser.cc                          src/h264_rtp_parser.cc
    src/h264_rtp_single_parser.cc                       src/h264_rtp_stapa_parser.cc
)

target_include_directories (h264nal PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
