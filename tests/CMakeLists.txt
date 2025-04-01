# tests/CMakeLists.txt
add_executable(test_main test_main.cpp)

# Link the core library and dependencies
target_link_libraries(test_main PRIVATE
        CoreLib
        ${Boost_LIBRARIES}
        OpenSSL::SSL
        OpenSSL::Crypto
        pthread
)
