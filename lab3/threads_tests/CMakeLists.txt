cmake_minimum_required(VERSION 3.10)

# ������� ����� ��� �������
find_package(Threads REQUIRED)

# �������� ���� � Catch2
get_filename_component(CATCH_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../include" ABSOLUTE)

# ������� ����������� ���� ��� ������
add_executable(threads_tests threads_tests.cpp)

# �������� ���������� � ������������� �������
target_include_directories(threads_tests PRIVATE ${CATCH_INCLUDE_DIR})

# ���������� ���������� �������
target_link_libraries(threads_tests PRIVATE Threads::Threads)

# ������������� ���������� ��� ������
set_target_properties(threads_tests PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
)

# ��������� ����
add_test(NAME ThreadsTests COMMAND threads_tests)