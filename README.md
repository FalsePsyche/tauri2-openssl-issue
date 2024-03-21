# Example Tauri 2 Beta OpenSSL Windows issue

This repository is an example repository of the issues I am running into when trying to build and emulate an android app on a Windows machine. The problem package seems to be reqwest and its dependency openssl-sys.

The following is an example output of the issue I see

```sh
C:\repos\tauri2-openssl-issue (main -> origin)
λ pnpm tauri android dev

> tauri2-openssl@0.0.0 tauri C:\repos\tauri2-openssl-issue
> tauri "android" "dev"

    Info Detected connected device: Pixel_8_Pro_API_34 (sdk_gphone64_x86_64) with target "x86_64-linux-android"
    Info Using 192.168.1.71 to access the development server.
    Running BeforeDevCommand (`pnpm dev`)

> tauri2-openssl@0.0.0 dev C:\repos\tauri2-openssl-issue
> vite


  VITE v5.2.2  ready in 559 ms

  ➜  Local:   http://localhost:1420/
  ➜  Network: http://192.168.1.71:1420/
    Info detected host target triple "x86_64-pc-windows-msvc"
   Compiling openssl-sys v0.9.101
   Compiling tauri v2.0.0-beta.13
   Compiling wry v0.37.0
error: failed to run custom build command for `openssl-sys v0.9.101`

Caused by:
  process didn't exit successfully: `C:\repos\tauri2-openssl-issue\src-tauri\target\debug\build\openssl-sys-8fa6f915703aa3a1\build-script-main` (exit code: 101)
  --- stdout
  cargo:rerun-if-env-changed=X86_64_LINUX_ANDROID_OPENSSL_LIB_DIR
  X86_64_LINUX_ANDROID_OPENSSL_LIB_DIR unset
  cargo:rerun-if-env-changed=OPENSSL_LIB_DIR
  OPENSSL_LIB_DIR unset
  cargo:rerun-if-env-changed=X86_64_LINUX_ANDROID_OPENSSL_INCLUDE_DIR
  X86_64_LINUX_ANDROID_OPENSSL_INCLUDE_DIR unset
  cargo:rerun-if-env-changed=OPENSSL_INCLUDE_DIR
  OPENSSL_INCLUDE_DIR unset
  cargo:rerun-if-env-changed=X86_64_LINUX_ANDROID_OPENSSL_DIR
  X86_64_LINUX_ANDROID_OPENSSL_DIR unset
  cargo:rerun-if-env-changed=OPENSSL_DIR
  OPENSSL_DIR = C:\Program Files\OpenSSL-Win64
  cargo:rerun-if-changed=C:\Program Files\OpenSSL-Win64\include\openssl
  cargo:rustc-link-search=native=C:\Program Files\OpenSSL-Win64\lib
  cargo:include=C:\Program Files\OpenSSL-Win64\include
  cargo:rerun-if-changed=build/expando.c
  OPT_LEVEL = Some("0")
  TARGET = Some("x86_64-linux-android")
  HOST = Some("x86_64-pc-windows-msvc")
  cargo:rerun-if-env-changed=CC_x86_64-linux-android
  CC_x86_64-linux-android = None
  cargo:rerun-if-env-changed=CC_x86_64_linux_android
  CC_x86_64_linux_android = None
  cargo:rerun-if-env-changed=TARGET_CC
  TARGET_CC = Some("C:\\Users\\7tann\\AppData\\Local\\Android\\Sdk\\ndk\\26.2.11394342\\toolchains/llvm/prebuilt/windows-x86_64\\bin\\x86_64-linux-android24-clang.cmd")
  cargo:rerun-if-env-changed=CRATE_CC_NO_DEFAULTS
  CRATE_CC_NO_DEFAULTS = None
  DEBUG = Some("true")
  cargo:rerun-if-env-changed=CFLAGS_x86_64-linux-android
  CFLAGS_x86_64-linux-android = None
  cargo:rerun-if-env-changed=CFLAGS_x86_64_linux_android
  CFLAGS_x86_64_linux_android = None
  cargo:rerun-if-env-changed=TARGET_CFLAGS
  TARGET_CFLAGS = None
  cargo:rerun-if-env-changed=CFLAGS
  CFLAGS = None
  cargo:rerun-if-env-changed=CC_ENABLE_DEBUG_OUTPUT
  version: 3_2_1
  cargo:rustc-cfg=osslconf="OPENSSL_NO_SSL3_METHOD"
  cargo:conf=OPENSSL_NO_SSL3_METHOD
  cargo:rustc-cfg=openssl
  cargo:rustc-cfg=ossl320
  cargo:rustc-cfg=ossl300
  cargo:rustc-cfg=ossl101
  cargo:rustc-cfg=ossl102
  cargo:rustc-cfg=ossl102f
  cargo:rustc-cfg=ossl102h
  cargo:rustc-cfg=ossl110
  cargo:rustc-cfg=ossl110f
  cargo:rustc-cfg=ossl110g
  cargo:rustc-cfg=ossl110h
  cargo:rustc-cfg=ossl111
  cargo:rustc-cfg=ossl111b
  cargo:rustc-cfg=ossl111c
  cargo:rustc-cfg=ossl111d
  cargo:version_number=30200010
  cargo:rerun-if-env-changed=X86_64_LINUX_ANDROID_OPENSSL_LIBS
  X86_64_LINUX_ANDROID_OPENSSL_LIBS unset
  cargo:rerun-if-env-changed=OPENSSL_LIBS
  OPENSSL_LIBS unset
  cargo:rerun-if-env-changed=X86_64_LINUX_ANDROID_OPENSSL_STATIC
  X86_64_LINUX_ANDROID_OPENSSL_STATIC unset
  cargo:rerun-if-env-changed=OPENSSL_STATIC
  OPENSSL_STATIC unset

  --- stderr
  thread 'main' panicked at C:\Users\7tann\.cargo\registry\src\index.crates.io-6f17d22bba15001f\openssl-sys-0.9.101\build/main.rs:413:13:
  OpenSSL libdir at `["C:\\Program Files\\OpenSSL-Win64\\lib"]` does not contain the required files to either statically or dynamically link OpenSSL
  note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
warning: build failed, waiting for other jobs to finish...
 ELIFECYCLE  Command failed with exit code 4294967295.
    Error `Failed to run `cargo build`: command ["cargo", "build", "--package", "tauri2-openssl", "--manifest-path", "C:\\repos\\tauri2-openssl-issue\\src-tauri\\Cargo.toml", "--target", "x86_64-linux-android", "--lib"] exited with code 101
 ELIFECYCLE  Command failed with exit code 1.

```

## Tauri + Vanilla TS

This template should help get you started developing with Tauri in vanilla HTML, CSS and Typescript.

### Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Tauri](https://marketplace.visualstudio.com/items?itemName=tauri-apps.tauri-vscode) + [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer)

