# Microsoft Azure Standard D64s v6 (64 vcpu, 256 GiB RAM)

Machine sponsored by Kenji Mouri.

## Results

- 7-Zip ZS Benchmark (Running by Himi Misaki.)
  - Prebuilt binaries:
    [Intel C/C++ compiler, glibc & mimalloc](Micc-7zst.tar.xz)
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
- benchncnn (Running by Kenji Mouri.): [markdown](benchncnn.md)
- dmidecode (Running by Kenji Mouri.): [txt](dmidecode.txt)
- SPEC CPU 2006 (Running by Himi Misaki.)
  - `-march=native`
    - CINT2006: [pdf](CINT2006_native.pdf), [tar.gz](cint2006_native.tar.gz)
    - CFP2006: [pdf](CFP2006_native.pdf), [tar.gz](cfp2006_native.tar.gz)
  - `-march=native -mprefer-vector-width=512`
    - CINT2006 & CFP2006:
      [pdf (CINT2006)](CINT2006_avx512.pdf),
      [pdf (CFP2006)](CFP2006_avx512.pdf),
      [tar.gz](cpu2006_avx512.tar.gz)
    - CINT2006rate & CFP2006rate:
      [pdf (CINT2006rate)](CINT2006rate_avx512.pdf),
      [pdf (CFP2006rate)](CFP2006rate_avx512.pdf),
      [tar.gz](cpu2006rate_avx512.tar.gz)
  - `-march=sapphirerapids -mprefer-vector-width=512`
    - CINT2006 & CFP2006:
      [pdf (CINT2006)](CINT2006_spr_avx512.pdf),
      [pdf (CFP2006)](CFP2006_spr_avx512.pdf),
      [tar.gz](cpu2006_spr_avx512.tar.gz)
