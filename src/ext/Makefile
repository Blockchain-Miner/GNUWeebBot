#
# SPDX-License-Identifier: GPL-2.0
# 
# GNUWeebBot (GNUWeeb Telegram Bot)
# 
# https://github.com/GNUWeeb/GNUWeebBot
#

include $(BASE_DIR)/src/ext/criterion/Makefile
include $(BASE_DIR)/src/ext/inih/Makefile
include $(BASE_DIR)/src/ext/openssl_1.1.1j/Makefile

# __execute_make_io_uring:
# 	+$(Q)cd $(BASE_DIR)/src/ext/liburing-2.0 && $(MAKE) --no-print-directory;

# __clean_io_uring:
# 	+$(Q)cd $(BASE_DIR)/src/ext/liburing-2.0 && $(MAKE) --no-print-directory clean;

# LIB_LDFLAGS	+= -L$(BASE_DIR)/src/ext/liburing-2.0/src -luring
# SHARED_LIB	+= $(BASE_DIR)/src/ext/liburing-2.0/src/liburing.so.2.0.0

# $(BASE_DIR)/src/ext/liburing-2.0/src/liburing.so.2.0.0: __execute_make_io_uring


#
# JSON-C
#
SHARED_LIB	+= $(BASE_DIR)/src/ext/json-c/build.dir/libjson-c.so

LIB_LDFLAGS	+= \
	-L$(BASE_DIR)/src/ext/json-c/build.dir -ljson-c \
	-lmysqlclient

INCLUDE_DIR	+= \
	-I$(BASE_DIR)/src/ext/json-c \
	-I$(BASE_DIR)/src/ext/json-c/build.dir \
	-I$(BASE_DIR)/src/ext/mysql8/include


$(BASE_DIR)/src/ext/json-c/build.dir/libjson-c.so:
	+$(Q)cd  $(BASE_DIR)/src/ext/json-c && \
	mkdir -pv build.dir && \
	cd build.dir && \
	cmake CMAKE_C_FLAGS_RELEASE=1 .. && \
	$(MAKE) --no-print-directory;

build_json_c: $(BASE_DIR)/src/ext/json-c/build.dir/libjson-c.so



clean_json_c:
	$(Q)rm -rfv $(BASE_DIR)/src/ext/json-c/build.dir;



test_json_c: $(BASE_DIR)/src/ext/json-c/build.dir/libjson-c.so
	+$(Q)cd  $(BASE_DIR)/src/ext/json-c && \
	mkdir -pv build.dir && \
	cd build.dir && \
	cmake .. && \
	$(MAKE) test ARGS="-j$(JOBS)" --no-print-directory;


test_ext: test_json_c

#
# Clean all extension build
#
clean_ext: clean_json_c


.PHONY: build_json_c clean_json_c test_json_c clean_ext
