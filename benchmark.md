# google benchmark

Experimenting with googles benchmark on MLOAM

This is what I get for the initial results for `mloam::ScanRegistration()`
``` c++
2022-09-18T08:59:59-06:00
Running ./build/mloam_benchmarks
Run on (16 X 2300 MHz CPU s)
CPU Caches:
  L1 Data 32 KiB
  L1 Instruction 32 KiB
  L2 Unified 256 KiB (x8)
  L3 Unified 16384 KiB
Load Average: 2.68, 2.83, 2.80
----------------------------------------------------------------
Benchmark                      Time             CPU   Iterations
----------------------------------------------------------------
BM_ScanRegistration/0    9346658 ns      9332145 ns           76
BM_ScanRegistration/1    9497580 ns      9494485 ns           66
BM_ScanRegistration/2    9459296 ns      9450328 ns           67
BM_ScanRegistration/3   10014751 ns      9959941 ns           68
BM_ScanRegistration/4    9567419 ns      9561197 ns           66
BM_ScanRegistration/5    9766798 ns      9758557 ns           61
```

Not sure the difference between `Time` and `CPU`. Need to investigate that.

The `BM_ScanRegistration/0`, `BM_ScanRegistration/1`, ... is the benchmark running `mloam::ScanRegistration()` on a specific KITTI binary point cloud (0, 1, 2, etc.) 

I think `Iterations` is how many times benchmark ran the specific benchmark.

Is the `Time` normalized over `Iterations` or is it cummulative? Would make more sense if it was normalized.

---
Changing some code around and running benchmarks again I got these results

```
2022-09-18T09:08:01-06:00
Running ./build/mloam_benchmarks
Run on (16 X 2300 MHz CPU s)
CPU Caches:
  L1 Data 32 KiB
  L1 Instruction 32 KiB
  L2 Unified 256 KiB (x8)
  L3 Unified 16384 KiB
Load Average: 1.74, 2.29, 2.56
----------------------------------------------------------------
Benchmark                      Time             CPU   Iterations
----------------------------------------------------------------
BM_ScanRegistration/0    8840144 ns      8828986 ns           72
BM_ScanRegistration/1    8970913 ns      8964746 ns           67
BM_ScanRegistration/2    9376974 ns      9362294 ns           68
BM_ScanRegistration/3    9443818 ns      9433891 ns           64
BM_ScanRegistration/4    9491327 ns      9480118 ns           68
BM_ScanRegistration/5    9915625 ns      9907868 ns           68
```

This is about ~0.5 milliseconds savings. Insert sarcastic mic drop.

