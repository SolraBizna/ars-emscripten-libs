LUA_PATH=lua-5.3.4
ZLIB_PATH=zlib-1.2.11
LUA_SOURCES=$(addprefix $(LUA_PATH)/src/, \
	lapi.c lcode.c lctype.c ldebug.c ldo.c ldump.c lfunc.c lgc.c llex.c \
	lmem.c lobject.c lopcodes.c lparser.c lstate.c lstring.c ltable.c \
	ltm.c lundump.c lvm.c lzio.c lauxlib.c)
ZLIB_SOURCES=$(addprefix $(ZLIB_PATH)/, \
	adler32.c crc32.c deflate.c infback.c inffast.c inflate.c inftrees.c \
	trees.c zutil.c)

all: ars-emscripten-libs.bc lua.h lualib.h lauxlib.h zlib.h zconf.h

ars-emscripten-libs.bc:
	rm -f $(LUA_PATH)/src/luaconf.h
	emcc -DRELEASE=1 -DNDEBUG=1 -O3 -flto -I. \
	-I$(LUA_PATH)/src $(LUA_SOURCES) \
	-I$(ZLIB_PATH)/ $(ZLIB_SOURCES) \
	-o $@

%.h: $(LUA_PATH)/src/%.h
	cp $< $@

%.h: $(ZLIB_PATH)/%.h
	cp $< $@

clean:
	rm -f ars-emscripten-libs.bc lua.h lualib.h lauxlib.h zlib.h
