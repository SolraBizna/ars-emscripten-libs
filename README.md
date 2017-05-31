This is Lua 5.3.4 and zlib 1.2.11, packaged in the way expected by the ARS-emu Emscripten target. They are licensed under their respective license. Any part of this repository that doesn't come from the Lua or zlib packages is in the public domain.

(I didn't know about Emscripten's Ports when I began the port, so I didn't even check if Lua and zlib were already there in the correct versions.)

# Building

Set up the Emscripten SDK as normal. Then cd to this directory and run make. That's it.

ARS-emu's Emscripten port expects to find the (built) ars-emscripten-libs directory adjacent to the ars-emu directory.
