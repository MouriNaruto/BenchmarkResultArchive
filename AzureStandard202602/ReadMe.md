# Microsoft Azure Standard Benchmarks (February 2026)

All instances are sponsored by Kenji Mouri.

All instances are 64 vcpu, 256 GiB RAM, and 256 GiB OS Disk.

All rate series SPEC CPU 2006 benchmark uses `copies=64`.

## Prebuilt Binaries

- Intel C/C++ compiler, glibc & mimalloc (for x64):
  [flags](Binaries/icc-flags.txt)
  [binaries](Binaries/Micc-7zst.tar)

## Detailed Results

### Microsoft Azure Standard D64ps v6 (64 vcpu, 256 GiB RAM)

- 7-Zip Benchmark (Running by Himi Misaki.)
  - glibc allocator: [txt](D64ps_v6/7zb.txt)
  - mimalloc allocator: [txt](D64ps_v6/m7zb.txt)
- benchncnn (Running by Kenji Mouri.): [markdown](D64ps_v6/benchncnn.md)
- SPEC CPU 2006 (Running by Himi Misaki.)
  - Configuration: [cfg.proj](D64ps_v6/gcc-linux-arm64.cfg.proj)
  - CINT2006:
    [pdf](D64ps_v6/CINT2006.pdf),
    [tar](D64ps_v6/cint2006.tar)
  - CFP2006:
    [pdf](D64ps_v6/CFP2006.pdf),
    [tar](D64ps_v6/cfp2006.tar)
  - CINT2006rate:
    [pdf](D64ps_v6/CINT2006rate.pdf),
    [tar](D64ps_v6/cint2006rate.tar)
  - CFP2006rate:
    [pdf](D64ps_v6/CFP2006rate.pdf),
    [tar](D64ps_v6/cfp2006rate.tar)

### Microsoft Azure Standard D64s v6 (64 vcpu, 256 GiB RAM)

- 7-Zip ZS Benchmark (Running by Himi Misaki.)
  - glibc allocator:
    [txt (GCC)](D64s_v6/g7zsb.txt)
    [txt (Clang)](D64s_v6/c7zsb.txt)
    [txt (Intel C/C++ compiler, SSE4.2)](D64s_v6/i7zssse4b.txt)
    [txt (Intel C/C++ compiler, AVX2)](D64s_v6/i7zsavx2b.txt)
    [txt (Intel C/C++ compiler, AVX-512)](D64s_v6/i7zsavx512b.txt)
    [txt (Intel C/C++ compiler, Zen 4)](D64s_v6/i7zszen4b.txt)
  - mimalloc allocator:
    [txt (Intel C/C++ compiler, SSE4.2)](D64s_v6/mi7zssse4b.txt)
    [txt (Intel C/C++ compiler, AVX2)](D64s_v6/mi7zsavx2b.txt)
    [txt (Intel C/C++ compiler, AVX-512)](D64s_v6/mi7zsavx512b.txt)
    [txt (Intel C/C++ compiler, Zen 4)](D64s_v6/mi7zszen4b.txt)
- benchncnn (Running by Kenji Mouri.): [markdown](D64s_v6/benchncnn.md)
- dmidecode (Running by Kenji Mouri.): [txt](D64s_v6/dmidecode.txt)
- SPEC CPU 2006 (Running by Himi Misaki.)
  - Configuration: [cfg.proj](D64s_v6/gcc-linux-amd64.cfg.proj)
  - `-march=native`
    - CINT2006:
      [pdf](D64s_v6/CINT2006_native.pdf),
      [tar](D64s_v6/cint2006_native.tar)
    - CFP2006:
      [pdf](D64s_v6/CFP2006_native.pdf),
      [tar](D64s_v6/cfp2006_native.tar)
    - CINT2006rate:
      [pdf](D64s_v6/CINT2006rate_native.pdf),
      [tar](D64s_v6/cint2006rate_native.tar)
    - CFP2006rate:
      [pdf](D64s_v6/CFP2006rate_native.pdf),
      [tar](D64s_v6/cfp2006rate_native.tar)
  - `-march=native -mprefer-vector-width=512`
    - CINT2006 & CFP2006:
      [pdf (CINT2006)](D64s_v6/CINT2006_avx512.pdf),
      [pdf (CFP2006)](D64s_v6/CFP2006_avx512.pdf),
      [tar](D64s_v6/cpu2006_avx512.tar)
    - CINT2006rate & CFP2006rate:
      [pdf (CINT2006rate)](D64s_v6/CINT2006rate_avx512.pdf),
      [pdf (CFP2006rate)](D64s_v6/CFP2006rate_avx512.pdf),
      [tar](D64s_v6/cpu2006rate_avx512.tar)
  - `-march=sapphirerapids -mprefer-vector-width=512`
    - CINT2006 & CFP2006:
      [pdf (CINT2006)](D64s_v6/CINT2006_spr_avx512.pdf),
      [pdf (CFP2006)](D64s_v6/CFP2006_spr_avx512.pdf),
      [tar](D64s_v6/cpu2006_spr_avx512.tar)

### Microsoft Azure Standard D64as v7 (64 vcpu, 256 GiB RAM)

- 7-Zip ZS Benchmark (Running by Himi Misaki.)
  - glibc allocator:
    [txt (GCC)](D64as_v7/g7zsb.txt)
    [txt (Clang)](D64as_v7/c7zsb.txt)
    [txt (Intel C/C++ compiler, SSE4.2)](D64as_v7/i7zssse4b.txt)
    [txt (Intel C/C++ compiler, AVX2)](D64as_v7/i7zsavx2b.txt)
    [txt (Intel C/C++ compiler, AVX-512)](D64as_v7/i7zsavx512b.txt)
    [txt (Intel C/C++ compiler, Zen 4)](D64as_v7/i7zszen4b.txt)
  - mimalloc allocator:
    [txt (Intel C/C++ compiler, SSE4.2)](D64as_v7/mi7zssse4b.txt)
    [txt (Intel C/C++ compiler, AVX2)](D64as_v7/mi7zsavx2b.txt)
    [txt (Intel C/C++ compiler, AVX-512)](D64as_v7/mi7zsavx512b.txt)
    [txt (Intel C/C++ compiler, Zen 4)](D64as_v7/mi7zszen4b.txt)
- benchncnn (Running by Kenji Mouri.): [markdown](D64as_v7/benchncnn.md)
- SPEC CPU 2006 (Running by Himi Misaki.)
  - Configuration: [cfg.proj](D64as_v7/gcc-linux-amd64.cfg.proj)
  - `-march=native`
    - CINT2006:
      [pdf](D64as_v7/CINT2006_native.pdf),
      [tar](D64as_v7/cint2006_native.tar)
    - CFP2006:
      [pdf](D64as_v7/CFP2006_native.pdf),
      [tar](D64as_v7/cfp2006_native.tar)
    - CINT2006rate:
      [pdf](D64as_v7/CINT2006rate_native.pdf),
      [tar](D64as_v7/cint2006rate_native.tar)
    - CFP2006rate:
      [pdf](D64as_v7/CFP2006rate_native.pdf),
      [tar](D64as_v7/cfp2006rate_native.tar)
  - `-march=native -mprefer-vector-width=512`
    - CINT2006:
      [pdf](D64as_v7/CINT2006_avx512.pdf),
      [tar](D64as_v7/cint2006_avx512.tar)
    - CFP2006:
      [pdf](D64as_v7/CFP2006_avx512.pdf),
      [tar](D64as_v7/cfp2006_avx512.tar)
    - CINT2006rate:
      [pdf](D64as_v7/CINT2006rate_avx512.pdf),
      [tar](D64as_v7/cint2006rate_avx512.tar)
    - CFP2006rate:
      [pdf](D64as_v7/CFP2006rate_avx512.pdf),
      [tar](D64as_v7/cfp2006rate_avx512.tar)
