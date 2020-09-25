# License: Boost 1.0
# By Paul Dreik 2020

add_executable(fuzz_TestSpecParser fuzz_TestSpecParser.cpp)
target_link_libraries(fuzz_TestSpecParser PRIVATE Catch2::Catch2)

add_executable(fuzz_XmlWriter fuzz_XmlWriter.cpp)
target_link_libraries(fuzz_XmlWriter PRIVATE Catch2::Catch2)

# This should be possible to set from the outside to be oss-fuzz compatible,
# fix later. For now, be libFuzzer only.
target_link_options(fuzz_TestSpecParser PRIVATE "-fsanitize=fuzzer")
target_link_options(fuzz_XmlWriter PRIVATE "-fsanitize=fuzzer")
