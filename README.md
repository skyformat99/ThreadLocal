# ThreadLocal
Portable and implementation configurable `c++11` like thread local. The same code supports different implementations controlled by macro `USE_STD_THREAD_LOCAL`.

The default implementation of macro `THREAD_LOCAL(...)` is c++11 `thread_local` keyword if supported. Otherwise, pthread and FLS implementation is used.

## WHY
`c++11` **thread_local** is not available for vs2013, apple clang for iOS (and macOS if xcode < 8), libc++ in android ndk < r14.

## Tested Compilers
VS2013, VS2015, gcc>=4.7, clang >=3.4, Apple clang

## Build

- `g++/clang++` `c++11` thread_local: `(clan)g++ -std=c++11 test.cpp`
- `g++/clang++` pthread implementation: `(clan)g++ -std=c++11 test.cpp -DUSE_STD_THREAD_LOCAL=0`
- apple clang (pthread implementation): `clang++ -std=c++11 test.cpp`
- vs2015 `c++11` thread_local: `cl /EHsc test.cpp`
- vs2015 FLS implementation: `cl /EHsc test.cpp -DUSE_STD_THREAD_LOCAL=0`
- vs2013 (FLS implementation): `cl /EHsc test.cpp`
- mingw `c++11` thread_local: `g++ -std=c++11 test.cpp`
- mingw FLS implementation: `g++ -std=c++11 test.cpp -D_WIN32_WINNT=0x0600 -DUSE_STD_THREAD_LOCAL=0`
- mingw pthread implementation: `g++ -std=c++11 test.cpp -DUSE_STD_THREAD_LOCAL=0`
