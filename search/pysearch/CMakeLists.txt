project(pysearch)

set(
  SRC
  bindings.cpp
)

include_directories(${CMAKE_BINARY_DIR})

omim_add_library(${PROJECT_NAME} MODULE ${SRC})

omim_link_libraries(
  ${PROJECT_NAME}
  search_quality
  search_tests_support
  search
  storage
  editor
  indexer
  geometry
  ge0
  platform
  mwm_diff
  coding
  base
  bsdiff
  icu
  jansson
  oauthcpp
  opening_hours
  protobuf
  pugixml
  succinct
  ${Boost_LIBRARIES}
  ${LIBZ}
)

link_qt5_core(${PROJECT_NAME})
link_qt5_network(${PROJECT_NAME})

if (PLATFORM_MAC)
  omim_link_libraries(${PROJECT_NAME} "-Wl,-undefined,dynamic_lookup")
endif()

set_target_properties(${PROJECT_NAME} PROPERTIES PREFIX "")
