cmake_minimum_required(VERSION 3.29)
project(BlockChain)

set(CMAKE_CXX_STANDARD 20)

# Create a sources variable with a link to all cpp files to compile
file(GLOB CPP_MAIN "*.cpp")
file(GLOB CPP_SOURCES "src/*.cpp")
file(GLOB H_SOURCES "src/*.h")

file(GLOB H_BLOCK_CHAIN_CORE "src/BlockChainCore/*.h")
file(GLOB CPP_BLOCK_CHAIN_CORE "src/BlockChainCore/*.cpp")

file(GLOB H_MINING "src/Mining/*.h")
file(GLOB CPP_MINING "src/Mining/*.cpp")

file(GLOB H_P2P "src/P2P/*.h")
file(GLOB CPP_P2P "src/P2P/*.cpp")

file(GLOB H_UI "src/UI/*.h")
file(GLOB CPP_UI "src/UI/*.cpp")

file(GLOB H_WALLET "src/Wallet/*.h")
file(GLOB CPP_WALLET "src/Wallet/*.cpp")

set(BOOST_ROOT "C:/boost")
set(Boost_INCLUDE_DIRS ${BOOST_ROOT}/include/boost-1_86/boost)
set(Boost_LIBRARY_DIR ${BOOST_ROOT}/lib)
set(Boost_USE_STATIC_LIBS ON)

find_package(Boost)

add_executable(${PROJECT_NAME}
        ${HPP_SOURCES}
        ${H_SOURCES}
        ${CPP_SOURCES}
        ${CPP_MAIN}

        ${H_BLOCK_CHAIN_CORE}
        ${CPP_BLOCK_CHAIN_CORE}

        ${H_MINING}
        ${CPP_MINING}

        ${H_P2P}
        ${CPP_P2P}

        ${H_UI}
        ${CPP_UI}

        ${H_WALLET}
        ${CPP_WALLET})

target_include_directories(${PROJECT_NAME} PRIVATE ${Boost_INCLUDE_DIRS})

target_link_libraries(${PROJECT_NAME} PRIVATE
        ${Boost_LIBRARY_DIR}/libboost_system-mgw14-mt-x64-1_86.a
        ${Boost_LIBRARY_DIR}/libboost_thread-mgw14-mt-x64-1_86.a
        ws2_32
        mswsock
)