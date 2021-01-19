## Call C++ from Rust using shared library method

In this app, [src/main.rs](https://github.com/simsekgokhan/rust_call_cpp_so/blob/main/src/main.rs) calls C++ function `void say_hello(std::string const& str, int reps)` from [libhello_cpp/hello.cpp](https://github.com/simsekgokhan/rust_call_cpp_so/blob/main/libhello_cpp/hello.cpp).
  
  
### How to use  

```
Ubuntu 20.04

// 1. Edit libhello_cpp/hello.cpp as you like

// 2. Create C++ shared library for libhello_cpp/hello.cpp 
cd libhello_cpp
g++ -shared -fPIC -o libhello.so hello.cpp 

// 3. Put your dependency into build.rs
println!("cargo:rustc-link-search=native=/home/gsimsek/rust_call_cpp/libhello_cpp/");        
println!("cargo:rustc-link-lib=dylib=hello"); 
    
// 4. Run rust app
$ cargo r
Hello from C++ say_hello()
  // main.rs calling C++ function -
  // void say_hello(std::string const& str, int reps) -
  // from libhello_cpp/hello.cpp 

```

### Sources
https://crates.io/crates/cc  
https://www.youtube.com/watch?v=iCZkqDMJiF8  

