#
# SPDX-License-Identifier: GPL-2.0
# 
# GNUWeebBot (GNUWeeb Telegram Bot)
# 
# https://github.com/GNUWeeb/GNUWeebBot
#


INCLUDE_DIR += -I$(BASE_DIR)/src/ext/criterion/include
DEP_DIRS	+= $(BASE_DEP_DIR)/src/ext/criterion

ifeq ($(DO_TEST),1)
	TEST_LIB_LDFLAGS = -L$(BASE_DIR)/src/ext/criterion/lib -lcriterion $(LIB_LDFLAGS)
	LD_LIBRARY_PATH=$(BASE_DIR)/src/ext/criterion/lib
	LD_PRELOAD=$(BASE_DIR)/src/ext/criterion/lib/libcriterion.so.3.1.0
	export LD_PRELOAD
	export LD_LIBRARY_PATH
endif
