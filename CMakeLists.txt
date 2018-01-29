cmake_minimum_required(VERSION 3.9)
project(web_server_cpprest)

set(CMAKE_CXX_STANDARD 17)
find_package (Threads)
find_package(OpenSSL 1.0.2 REQUIRED)

find_package(Boost REQUIRED COMPONENTS system thread log program_options chrono)
add_executable(web_server_cpprest main.cpp)
include_directories(${Boost_INCLUDDIR})
target_link_libraries(web_server_cpprest cpprest ${CMAKE_THREAD_LIBS_INIT} ${Boost_LIBRARIES})
message("openssl libs: "${OPENSSL_FOUND})
target_link_libraries(web_server_cpprest  ${OPENSSL_LIBS} ${OPENSSL_CRYPTO_LIBRARY} ${OPENSSL_SSL_LIBRARY})