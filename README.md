# dv.manager Windows Compile Test

Minimal repository to verify whether **dv.manager 3.1.0** compiles on Windows vs Linux.

## What it tests

GitHub Actions installs `Boehringer-Ingelheim/dv.manager` (latest tag, currently 3.1.0) on:

| Runner | Expected result (as of 2026-07) |
|--------|----------------------------------|
| `ubuntu-latest` | Success |
| `windows-latest` | Fail (`aligned_alloc` on MinGW/Rtools) |

## How to run

1. Push this repo to GitHub.
2. Open **Actions** → **Test dv.manager 3.1.0 compile** → **Run workflow**.
3. Compare the two matrix jobs.

## Local Windows check (optional)

```r
install.packages("pak", repos = "https://cloud.r-project.org")
pak::pak("Boehringer-Ingelheim/dv.manager")
```

## References

- Failing API: `aligned_alloc()` in `src/binary_serialize_ints.c`
- Windows toolchain: Rtools45 + GCC (MinGW)
