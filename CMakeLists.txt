project (yojimbo)

add_library(
  yojimbo
  yojimbo.cpp
  yojimbo.h
  yojimbo_address.cpp
  yojimbo_address.h
  yojimbo_bitpack.h
  yojimbo_allocator.cpp
  yojimbo_allocator.h
  yojimbo_bit_array.h
  yojimbo_channel.cpp
  yojimbo_channel.h
  yojimbo_client.cpp
  yojimbo_client.h
  yojimbo_client_server_packets.h
  yojimbo_common.cpp
  yojimbo_common.h
  yojimbo_config.h
  yojimbo_connection.cpp
  yojimbo_connection.h
  yojimbo_encryption.cpp
  yojimbo_encryption.h
  yojimbo_matcher.cpp
  yojimbo_matcher.h
  yojimbo_message.h
  yojimbo_network.cpp
  yojimbo_network.h
  yojimbo_network_simulator.cpp
  yojimbo_network_simulator.h
  yojimbo_packet.cpp
  yojimbo_packet.h
  yojimbo_packet_processor.cpp
  yojimbo_packet_processor.h
  yojimbo_platform.cpp
  yojimbo_platform.h
  yojimbo_queue.h
  yojimbo_replay_protection.h
  yojimbo_sequence_buffer.h
  yojimbo_serialize.h
  yojimbo_server.cpp
  yojimbo_server.h
  yojimbo_sockets.cpp
  yojimbo_sockets.h
  yojimbo_stream.h
  yojimbo_tlsf.cpp
  yojimbo_tlsf.h
  yojimbo_tokens.cpp
  yojimbo_tokens.h
  yojimbo_transport.cpp
  yojimbo_transport.h
  )

include_directories(windows/sodium windows .)

link_directories(
  ${CMAKE_SOURCE_DIR}/windows
  )

target_link_libraries(
  yojimbo
  sodium-release
  mbedtls-release
  mbedcrypto-release
  mbedx509-release
  )

add_executable(
  yojimbo_test
  yojimbo
  tests/test.cpp
  )

target_link_libraries(
  yojimbo_test
  yojimbo
  )

add_executable(
  yojimbo_info
  yojimbo
  tests/info.cpp
  )

target_link_libraries(
  yojimbo_info
  yojimbo
  )

add_executable(
  yojimbo_client
  yojimbo
  tests/client.cpp
  )

target_link_libraries(
  yojimbo_client
  yojimbo
  )

add_executable(
  yojimbo_secure_client
  yojimbo
  tests/secure_client.cpp
  )
  
target_compile_definitions( yojimbo_secure_client PRIVATE YOJIMBO_SECURE_MODE=1)

target_link_libraries(
  yojimbo_secure_client
  yojimbo
  )

 add_executable(
  yojimbo_server
  yojimbo
  tests/server.cpp
  )

target_link_libraries(
  yojimbo_server
  yojimbo
  )

add_executable(
  yojimbo_secure_server
  yojimbo
  tests/secure_server.cpp
  )

target_compile_definitions( yojimbo_secure_server PRIVATE SECURE_SERVER=1)

target_link_libraries(
  yojimbo_secure_server
  yojimbo
  )

add_executable(
  yojimbo_client_server
  yojimbo
  tests/client_server.cpp
  )

target_link_libraries(
  yojimbo_client_server
  yojimbo
  )

add_executable(
  yojimbo_soak
  tests/soak.cpp
  )

target_link_libraries(
  yojimbo_soak
  yojimbo
  )

add_executable(
  yojimbo_profile
  tests/profile.cpp
  )

target_link_libraries(
  yojimbo_profile
  yojimbo
  )
