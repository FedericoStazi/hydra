project(marshall)

add_library(${PROJECT_NAME} STATIC marshall.cc)

target_link_libraries(${PROJECT_NAME}
        PRIVATE
        db log worker
        )

add_library(libs::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
        PUBLIC
        $<INSTALL_INTERFACE:include>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        /usr/include/postgres
        PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}
        )


target_compile_features(${PROJECT_NAME}
        PRIVATE
        cxx_std_11
        )