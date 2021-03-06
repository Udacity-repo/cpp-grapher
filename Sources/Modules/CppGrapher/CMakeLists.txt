add_subdirectory(Deserialization)
add_subdirectory(Validation)
add_subdirectory(Visualization)

set(SOURCE_FILES
        CppGrapher.cpp
        CppGrapher.h
        ${VALIDATION_SOURCE_FILES}
        ${DESERIALIZATION_SOURCE_FILES}
        ${VISUALIZATION_SOURCE_FILES}
        ${THIRD_PARTY_SOURCE_FILES}
        ${HELPERS_SOURCE_FILES}
        ../RangedGraph/RangedGraph.cpp
        ../RangedGraph/RangedGraph.h)

add_library(CppGrapher ${SOURCE_FILES})

target_compile_definitions(CppGrapher PRIVATE MAGICKCORE_QUANTUM_DEPTH=8 MAGICKCORE_HDRI_ENABLE)

target_include_directories(CppGrapher PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/
        ${CMAKE_CURRENT_SOURCE_DIR}/../
        ${CMAKE_CURRENT_SOURCE_DIR}/../3rdParty/
        /usr/local/include/ImageMagick-7/)

target_link_libraries (CppGrapher PUBLIC RangedGraph Magick++-7.Q8HDRI)
