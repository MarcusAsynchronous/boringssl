include_directories(../../include)

add_library(
  evp

  OBJECT

  digestsign.c
  evp.c
  evp_asn1.c
  evp_ctx.c
  p_dsa_asn1.c
  p_ec.c
  p_ec_asn1.c
  p_ed25519.c
  p_ed25519_asn1.c
  p_rsa.c
  p_rsa_asn1.c
  pbkdf.c
  print.c
  sign.c
)


add_executable(
  evp_test

  evp_test.cc

  $<TARGET_OBJECTS:test_support>
)

add_executable(
  pbkdf_test

  pbkdf_test.cc

  $<TARGET_OBJECTS:test_support>
)

target_link_libraries(evp_test crypto)
target_link_libraries(pbkdf_test crypto)
add_dependencies(all_tests evp_test pbkdf_test)
