# CMakeList.txt : 最上位の CMake プロジェクトファイル
# グローバル構成を行う
# また、サブプロジェクトをここに含める

cmake_minimum_required (VERSION 3.31)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# サポートされている場合は、MSVC コンパイラのホットリロードを有効にする
if (POLICY CMP0141)
    cmake_policy(SET CMP0141 NEW)
    set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("roguelike_robot")

# サブプロジェクト
add_subdirectory ("directx12_framework")
add_subdirectory ("roguelike_robot")
add_subdirectory ("tests")
