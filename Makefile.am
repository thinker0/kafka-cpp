## LibKafkaConect
## A C++ shared libray for connecting to Kafka

#
# Warning this is the first time I've made a configure.ac/Makefile.am thing
# Please improve it as I have no idea what I am doing
# @benjamg
#

ACLOCAL_AMFLAGS = -I build-aux/m4 ${ACLOCAL_FLAGS}
AM_CPPFLAGS = $(DEPS_CFLAGS)
EXAMPLE_LIBS = $(BOOST_SYSTEM_LIB) $(BOOST_THREAD_LIB) -lkafkaconnect

#
# Shared Library
#

lib_LTLIBRARIES = libkafkaconnect.la

libkafkaconnect_la_SOURCES = src/producer.cpp
libkafkaconnect_la_LDFLAGS = -version-info $(KAFKACONNECT_VERSION)

kafkaconnect_includedir = $(includedir)/kafkaconnect
kafkaconnect_include_HEADERS = src/producer.hpp \
	src/encoder.hpp \
	src/encoder_helper.hpp

#
# Examples
#                                 

noinst_PROGRAMS = producer

producer_SOURCES = src/example.cpp
producer_LDADD = $(DEPS_LIBS) $(EXAMPLE_LIBS)

#
# Tests
#

check_PROGRAMS = tests/encoder_helper \
	tests/encoder \
	tests/producer \
	tests/producer_error

TESTS = ${check_PROGRAMS}

tests_encoder_helper_SOURCES = src/tests/encoder_helper_tests.cpp
tests_encoder_helper_LDADD = $(DEPS_LIBS) $(EXAMPLE_LIBS) $(BOOST_UNIT_TEST_FRAMEWORK_LIB)

tests_encoder_SOURCES = src/tests/encoder_tests.cpp
tests_encoder_LDADD = $(DEPS_LIBS) $(EXAMPLE_LIBS) $(BOOST_UNIT_TEST_FRAMEWORK_LIB)

tests_producer_SOURCES = src/tests/producer_tests.cpp
tests_producer_LDADD = $(DEPS_LIBS) $(EXAMPLE_LIBS) $(BOOST_UNIT_TEST_FRAMEWORK_LIB)

tests_producer_error_SOURCES = src/tests/producer_error_tests.cpp
tests_producer_error_LDADD = $(DEPS_LIBS) $(EXAMPLE_LIBS) $(BOOST_UNIT_TEST_FRAMEWORK_LIB)
