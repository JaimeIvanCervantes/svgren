include prorab.mk

this_name := tests

this_cxxflags += -g
this_cxxflags += -Wall
this_cxxflags += -Wno-format #no warnings about format
this_cxxflags += -DDEBUG
this_cxxflags += -fstrict-aliasing #strict aliasing!!!
this_cxxflags += -std=c++11

this_srcs += main.cpp

this_ldlibs += -lsvgdom $(d)../../src/libsvgren$(soext) -lpapki -lpng `pkg-config --libs cairo` -lstdc++
this_ldflags += -L$(d)../../src

ifeq ($(os), macosx)
    this_cxxflags += -stdlib=libc++ #this is needed to be able to use c++11 std lib
    this_ldlibs += -lc++
else ifeq ($(os),windows)
    this_ldlibs += -lpugixml
else
    this_ldlibs += -lX11
endif

$(eval $(prorab-build-app))


#ifeq ($(prorab_os),windows)
#    this_test_cmd := $(prorab_echo)(cd $(d); cp ../../src/libsvgren$(soext) .; $$^)
#else
#    this_test_cmd := $(prorab_echo)(cd $(d); LD_LIBRARY_PATH=../../src $$^)
#endif


#define this_rules
#test:: $(prorab_this_name)
#	@echo running $$^...
#	$(this_test_cmd)
#endef
#$(eval $(this_rules))

#add dependency on libsvgren
$(prorab_this_name): $(abspath $(d)../../src/libsvgren$(soext))

$(eval $(call prorab-include,$(d)../../src/makefile))
