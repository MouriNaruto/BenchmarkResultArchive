# Microsoft Azure Standard D64as v7 (64 vcpu, 256 GiB RAM)

Machine sponsored by Kenji Mouri.

## Results

- 7-Zip ZS Benchmark (Running by Himi Misaki.)
  - Intel C/C++ compiler, glibc & mimalloc Prebuilt binaries:
    [flags](icc-flags.txt)
    [binaries](Micc-7zst.tar)
  - glibc allocator:
    [txt (GCC)](g7zsb.txt)
    [txt (Clang)](c7zsb.txt)
    [txt (Intel C/C++ compiler, SSE4.2)](i7zssse4b.txt)
    [txt (Intel C/C++ compiler, AVX2)](i7zsavx2b.txt)
    [txt (Intel C/C++ compiler, AVX-512)](i7zsavx512b.txt)
    [txt (Intel C/C++ compiler, Zen 4)](i7zszen4b.txt)
  - mimalloc allocator:
    [txt (Intel C/C++ compiler, SSE4.2)](mi7zssse4b.txt)
    [txt (Intel C/C++ compiler, AVX2)](mi7zsavx2b.txt)
    [txt (Intel C/C++ compiler, AVX-512)](mi7zsavx512b.txt)
    [txt (Intel C/C++ compiler, Zen 4)](mi7zszen4b.txt)
- SPEC CPU 2006 (Running by Himi Misaki.)
  - Configuration: [cfg.proj](gcc-linux-amd64.cfg.proj)
  - `-march=native`
    - CINT2006: [pdf](CINT2006_native.pdf), [tar](cint2006_native.tar)
    - CFP2006: [pdf](CFP2006_native.pdf), [tar](cfp2006_native.tar)
    - CINT2006rate: [pdf](CINT2006rate_native.pdf), [tar](cint2006rate_native.tar)
    - CFP2006rate: [pdf](CFP2006rate_native.pdf), [tar](cfp2006rate_native.tar)
  - `-march=native -mprefer-vector-width=512`
    - CINT2006: [pdf](CINT2006_avx512.pdf), [tar](cint2006_avx512.tar)
    - CFP2006: [pdf](CFP2006_avx512.pdf), [tar](cfp2006_avx512.tar)
    - CINT2006rate: [pdf](CINT2006rate_avx512.pdf), [tar](cint2006rate_avx512.tar)
    - CFP2006rate: [pdf](CFP2006rate_avx512.pdf), [tar](cfp2006rate_avx512.tar)
