# nativelite

**Attack surface reduction through native tools and zero dependencies.**

Nativelite builds lightweight, focused libraries that eliminate unnecessary complexity by calling the operating system and standard library as a standard or expanding for specifics rather than broad.

## Philosophy

Every nativelite package starts with the same premise: **the OS is already a dependency you trust.** Rather than pulling in a crate/package ecosystem to handle a narrow concern with a wide net, we call the platform directly through safe, minimal interfaces.

See [nativelite-philosophy](https://github.com/nativelite/nativelite-philosophy) for the full charter, engineering standards, and design principles.

## Core packages

### IDs & Time-sortable UUIDs

- **[uid-rs](https://github.com/nativelite/uid-rs)** — ULID + UUIDv7 on Rust std
- **[uid-py](https://github.com/nativelite/uid-py)** — ULID + UUIDv7 on Python std
- **[uid-js](https://github.com/nativelite/uid-js)** — ULID + UUIDv7 on Node std

### Parsing & Data

- **[json-rs](https://github.com/nativelite/json-rs)** — RFC 8259 JSON parser/serializer (Rust std only)
- **[jsonheal-py](https://github.com/nativelite/jsonheal-py)** — Repair malformed JSON (Python std only)
- **[sse-py](https://github.com/nativelite/sse-py)** — Server-Sent Events parser (Python std only)
- **[patch-py](https://github.com/nativelite/patch-py)** — Unified diff apply & produce (Python std only)
- **[toml-rs](https://github.com/nativelite/toml-rs)** — TOML 1.0.0 parser (Rust std only)

### Terminal & TUI

- **[ansi-rs](https://github.com/nativelite/ansi-rs)** — ANSI/VT escape sequences as data (Rust std only)
- **[rawterm-rs](https://github.com/nativelite/rawterm-rs)** — Raw terminal mode via OS FFI (Rust std only)
- **[pty-rs](https://github.com/nativelite/pty-rs)** — Pseudo-terminal spawning (Rust std only)
- **[vterm-rs](https://github.com/nativelite/vterm-rs)** — Virtual terminal emulation
- **[agtop](https://github.com/nativelite/agtop)** — Live terminal monitor for agent sessions
- **[amux](https://github.com/nativelite/amux)** — Multi-agent terminal multiplexer

### Security & Secrets

- **[pwhash-py](https://github.com/nativelite/pwhash-py)** — Password hashing (scrypt, Python std only)
- **[otp-py](https://github.com/nativelite/otp-py)** — TOTP/HOTP one-time passwords (Python std only)
- **[jwt-hs-py](https://github.com/nativelite/jwt-hs-py)** — HMAC-signed JWTs (Python std only)
- **[cred-rs](https://github.com/nativelite/cred-rs)** — OS credential vault access (Rust std + FFI)
- **[akey](https://github.com/nativelite/akey)** — API key & WIF profile management

### Infrastructure

- **[fp-js](https://github.com/nativelite/fp-js)** — Browser fingerprinting (anti-bloat)
- **[fp-py](https://github.com/nativelite/fp-py)** — Browser fingerprinting (anti-bloat)
- **[web-server-rs](https://github.com/nativelite/web-server-rs)** — Lightweight webserver (zero external libraries) - coming soon
- **[web-server-py](https://github.com/nativelite/web-server-py)** — Lightweight webserver (zero external libraries) - coming soon
- **[agsess](https://github.com/nativelite/agsess)** — Agent session management

## Key principles

1. **Zero dependencies** — only std lib + OS APIs (via safe FFI when needed)  - the only caveat is if you plan to create an MVP -> Zero Deps based
2. **Attack surface by design** — every package is narrowly scoped; no feature creep
3. **Spec-anchored correctness** — tests anchor to specs (RFC 8259, RFC 6238, WHATWG), not just round-trips
4. **Cross-language mirrors** — same logic implemented in Rust, Python, JavaScript with byte-identical output
5. **One concern per package** — composable, not a monolith

## Development

Every nativelite package uses the same tooling:

```bash
python dev.py check   # zero-dependency guard + test suite (the pre-push gate)
python dev.py test    # run tests
python dev.py fmt     # check formatting
python dev.py guard   # verify no external dependencies
```

The `dev.py` runner is pure Python std lib, so `python dev.py check` works identically across Rust, Python, and JavaScript packages.

## Contributing

All work follows the philosophy and standards in [nativelite-philosophy](https://github.com/nativelite/nativelite-philosophy). Before proposing a new package or significant change, read the charter.

---

**Contact:** See individual repos for maintainer info and contribution guidelines.
