# Cheat Sheet: Random Number Generation in Modern C++ (`<random>`)

Concise and to the point — for quick orientation when developing serious tools.
---

## What it is and why
- `<random>` (C++11+) — modern library for pseudo- and (partially) hardware randomness.  
- Used for: simulations, games, tests, password/PIN generation (with caveats), statistics.  
- For **cryptography**, `<random>` itself does not provide guarantees; you need cryptographically secure sources and libraries.

---

## Main components (conceptually)
1. **Entropy source / seed** — initial value determining the sequence.  
   - `std::random_device rd;` — tries to get a “good” system source (e.g. `/dev/urandom`, WinAPI).  
2. **Generator (PRNG engine)** — produces a stream of pseudorandom bits.  
   - Examples: `std::mt19937` (32-bit), `std::mt19937_64` (64-bit), `std::minstd_rand0`, `std::ranlux48`.  
3. **Distribution** — maps generator bits into numbers in a desired range/distribution.  
   - `std::uniform_int_distribution<>` — uniform integers.  
   - `std::uniform_real_distribution<>` — uniform real numbers.  
   - `std::normal_distribution<>` — normal (Gaussian), etc.

---

## Recommendations
- For most tasks (speed + quality) → `std::mt19937` or `std::mt19937_64`.  
- If you need a larger period or 64-bit → choose `mt19937_64`.  
- For critical security keys → use dedicated APIs (OS crypto, OpenSSL, libsodium), not `mt19937`.

---

## Usage pattern (steps, without full code)
1. *Get seed*: `std::random_device rd;`  
2. *Initialize generator*: `std::mt19937 gen(rd());`  
3. *Create distribution*: `std::uniform_int_distribution<int> dist(min, max);`  
4. *Generate number*: `int x = dist(gen);`  
5. *For N numbers* — call `dist(gen)` in a loop.

> Note: `random_device` may be slow or pseudo-implemented on some platforms; still better than `time()`.

---

## Example ranges
- PIN (4 digits): `dist(0, 9999)` → format leading zeros separately.  
- Captcha / unique id: `dist(100000, 999999)` (6 digits).  
- Test values: `[1, 100]`, `[0, RAND_MAX]`, etc.

---

## Security notes
- `mt19937` is deterministic: knowing the seed allows recovery of the entire sequence.  
- For secure tasks (keys, tokens, passwords):  
  - Use `std::random_device` as a source (if OS ensures crypto strength), or  
  - use `CryptGenRandom` / `BCryptGenRandom` on Windows, `/dev/urandom` or libsodium/openssl on Unix.  
- Never use `rand()`/`srand()` for cryptographic purposes.

---

## Common mistakes
- **Not setting a range** for distributions — won’t work; always specify `min/max`.  
- **Seed = time(0) without cast** — MSVC warns; use `static_cast<unsigned int>(time(0))`, but better use `random_device`.  
- **Creating generator inside loop**: if you reinitialize `gen` with `random_device` every iteration, performance drops; create once and reuse.  
- **Weak seed source**: if `random_device` is pseudo, consider an external entropy source.

---

## Quick reference for types/functions
- `std::random_device rd;` — entropy source (may be slow/pseudo).  
- `std::mt19937 gen(rd());` — generator (32-bit).  
- `std::mt19937_64 gen64(rd());` — 64-bit generator.  
- `std::uniform_int_distribution<int> dist(a, b);` — uniform integers in `[a, b]`.  
- `std::uniform_real_distribution<double> dist(0.0, 1.0);` — uniform reals in `[0.0, 1.0]`.  
- Usage: `auto val = dist(gen);`

---

## Usage patterns (steps + scenarios)
### Generate N random numbers 1–100
1. Create `std::random_device rd;`
2. Create `std::mt19937 gen(rd());`
3. Create `std::uniform_int_distribution<int> dist(1, 100);`
4. Loop `for i in 0..N-1` — `print(dist(gen))`

### Generate PIN digits
1. Create `dist(0, 9)` and call 4 times, collecting digits.  
2. Alternative: `dist(0, 9999)` then print with leading zeros.

### If cryptographic strength needed
1. Don’t rely on `mt19937`.  
2. Use OS crypto API or libsodium: request random bytes and convert.

---

## Quick quality checks (practice)
- Validate generator with basic statistical tests (sum, mean, distribution by bins).  
- `mt19937` with `random_device` seed — sufficient for most non-critical tasks.

---

## Short checklist before use
- [ ] Defined required security level (game/test/keys)?  
- [ ] Chosen proper generator (`mt19937` / `mt19937_64` / crypto API)?  
- [ ] Distribution and range set explicitly?  
- [ ] Generator/distribution initialized once, not inside loops?  
- [ ] No `rand()`/`srand()` in new modules?  
- [ ] External crypto libs used if necessary?

---

## Further study
- Learn `std::random_device` behavior on your target OS (Windows vs Linux).  
- Explore other distributions: `normal_distribution`, `bernoulli_distribution`, `poisson_distribution`.  
- For crypto: study OpenSSL `RAND_bytes` or libsodium `randombytes_buf()`.
