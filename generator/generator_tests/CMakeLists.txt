project(generator_tests)

set(
  SRC
  affiliation_tests.cpp
  altitude_test.cpp
  brands_loader_test.cpp
  camera_collector_tests.cpp
  cells_merger_tests.cpp
  cities_boundaries_checker_tests.cpp
  cities_ids_tests.cpp
  city_roads_tests.cpp
  cluster_finder_tests.cpp
  coasts_test.cpp
  collector_boundary_postcode_tests.cpp
  collector_building_parts_tests.cpp
  collector_city_area_tests.cpp
  collector_routing_city_boundaries_tests.cpp
  common.cpp
  common.hpp
  complex_loader_tests.cpp
  cross_mwm_osm_ways_collector_tests.cpp
  descriptions_section_builder_tests.cpp
  feature_builder_test.cpp
  feature_merger_test.cpp
  filter_elements_tests.cpp
  gen_mwm_info_tests.cpp
  hierarchy_entry_tests.cpp
  hierarchy_tests.cpp
  intermediate_data_test.cpp
  maxspeeds_tests.cpp
  merge_collectors_tests.cpp
  metadata_parser_test.cpp
  metalines_tests.cpp
  mini_roundabout_tests.cpp
  node_mixer_test.cpp
  osm2meta_test.cpp
  osm_element_helpers_tests.cpp
  osm_o5m_source_test.cpp
  osm_type_test.cpp
  place_processor_tests.cpp
  restriction_collector_test.cpp
  restriction_test.cpp
  road_access_test.cpp
  source_data.cpp
  source_data.hpp
  source_to_element_test.cpp
  speed_cameras_test.cpp
  srtm_parser_test.cpp
  tag_admixer_test.cpp
  tesselator_test.cpp
  triangles_tree_coding_test.cpp
  types_helper.hpp
)

omim_add_test(${PROJECT_NAME} ${SRC})

omim_link_libraries(
  ${PROJECT_NAME}
  generator_tests_support
  platform_tests_support
  generator
  routing
  search
  storage
  traffic
  routing_common
  descriptions
  transit
  editor
  indexer
  platform
  geometry
  coding
  base
  expat
  icu
  jansson
  protobuf
  minizip
  succinct
  pugixml
  tess2
  oauthcpp
  opening_hours
  # TODO(syershov): Use FindPackage.
  sqlite3
  ${LIBZ}
)

if (PLATFORM_LINUX)
  omim_link_libraries(
    ${PROJECT_NAME}
    dl
  )
endif()

link_qt5_core(${PROJECT_NAME})
