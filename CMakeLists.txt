cmake_minimum_required(VERSION 3.10)

project(spdz_nec_ext_ring)
set(CMAKE_CXX_FLAGS "-g -O3 -std=c++14 -maes -mavx2 -fPIC")
set(SOURCE_FILES
	spdz2_ext_processor_Z2.cpp
	spdz2_ext_processor_Z2n.cpp
	spdzext.cpp
	spdz2_ext_processor_base.cpp
	NecReplicatedForSpdz/src/HashEncrypt.cpp
	NecReplicatedForSpdz/src/MPCParty.cpp
	NecReplicatedForSpdz/src/MalConfig.cpp
	NecReplicatedForSpdz/src/PRG.cpp
	NecReplicatedForSpdz/src/NecProtocolPartyBoolFor3P.cpp
	NecReplicatedForSpdz/src/NecProtocolPartyRingFor3P.cpp
)
add_library(spdz_nec_ext_ring SHARED ${SOURCE_FILES})
include_directories(NecReplicatedForSpdz/include)



target_link_libraries(	spdz_nec_ext_ring
			pthread
			dl
			z
			crypto
			ssl
)

