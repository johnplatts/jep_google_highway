## Release testing process

We run the following before a release:

### Windows x86 host

```
run_tests.bat
```

### Linux x86 host

Clang, GCC; Arm, PPC cross-compile: `./run_tests.sh`

Manual test of WASM and WASM_EMU256 targets.

Check libjxl build actions at https://github.com/libjxl/libjxl/pull/2269.

### Version updates

Prepend to debian/changelog and update mentions of the current version in:

*   base.h
*   CMakeLists.txt
*   MODULE.bazel
*   g3doc/faq.md

### Signing the release

*   `git archive --prefix=highway-X.Y.Z/ -o highway-X.Y.Z.tar.gz X.Y.Z`
*   `gpg --armor --detach-sign highway-X.Y.Z.tar.gz`
*   Edit release and attach the resulting `highway-X.Y.Z.tar.gz.asc` and .gz.

(See https://wiki.debian.org/Creating%20signed%20GitHub%20releases and search
hkps://keys.openpgp.org for janwas@google.com to obtain the key)
