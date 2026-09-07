# nativelite

**Lightweight packages built on native tools.** Maximum performance, minimum
bloat, zero third-party runtime dependencies, across modern languages.

## Why nativelite exists

nativelite was started by **Jeffrie Budde**
([@JSBtechnologies](https://github.com/JSBtechnologies)) out of a simple
frustration: reaching for a one-line task and watching the package manager pull
in a tree of hundreds of transitive dependencies, each one more code you did not
write, cannot audit, and now have to trust anyway.

The premise is that the operating system and the standard library are already
dependencies you trust. Most narrow problems (parse this, hash that, talk to a
terminal) can be solved by calling the platform directly through a small, safe
interface, instead of importing an ecosystem to do it. So that is what nativelite
does: one thing per package, done well, on top of what is already there.

Every package ships under the permissive MIT license. nativelite exists to give
the technology away.

## The non-negotiables

1. **Zero third-party runtime dependencies.** Standard library and OS APIs (via
   safe FFI when needed), nothing else. Some tools and applications built on
   nativelite are composed of several nativelite packages, which are themselves
   standard-library only, so the whole dependency tree stays free of third-party
   code. A dependency guard enforces this in every package.
2. **One concern per package.** A package does exactly one thing well. If it grows
   a second concern, that concern becomes its own package.
3. **Correctness first, then performance, then ergonomics**, in that order. A fast
   wrong answer is a bug. We benchmark and we prove.
4. **Spec-anchored tests.** Correctness is anchored to the spec (RFC 8259,
   RFC 6238, UAX #29, and so on), not just to round-trips.
5. **Small surface, honest docs.** The README never claims what the code does not
   do. Examples are runnable and tested.

## Packages

### Available now

The **atrium** suite is live on [crates.io](https://crates.io/crates/atrium): the
flagship terminal plus the ten zero-dependency crates it is built from, each
usable on its own. All Rust, standard library only. Install with
`cargo install atrium` for the app, or `cargo add <crate>` for a library.

| Crate | What it does |
| --- | --- |
| **[atrium](https://github.com/nativelite/atrium)** | tmux for coding agents: a multi-agent terminal |
| **[nativelite-abus](https://github.com/nativelite/abus)** | a coordination board and pub/sub bus for agent teams |
| **[nativelite-agsess](https://github.com/nativelite/agsess)** | local agent session state, read from coding-agent transcripts |
| **[nativelite-akey](https://github.com/nativelite/akey)** | API keys and Workload Identity Federation profiles for agent tooling |
| **[nativelite-ansi](https://github.com/nativelite/ansi-rs)** | ANSI/VT terminal output as data |
| **[nativelite-cred](https://github.com/nativelite/cred-rs)** | named secrets in the OS credential vault |
| **[nativelite-json](https://github.com/nativelite/json-rs)** | RFC 8259 JSON parser and serializer |
| **[nativelite-pty](https://github.com/nativelite/pty-rs)** | spawn a child on a real pseudo-terminal |
| **[nativelite-rawterm](https://github.com/nativelite/rawterm-rs)** | raw terminal mode and key/resize events via OS FFI |
| **[nativelite-uid](https://github.com/nativelite/uid-rs)** | time-sortable IDs (ULID + UUIDv7) |
| **[nativelite-vterm](https://github.com/nativelite/vterm-rs)** | a minimal terminal-emulator core |

### In progress

More packages, held to the same zero-dependency bar, not yet released:

- **duration** (Rust): parse and format human durations
- **uwidth** (Rust): grapheme-correct terminal text measurement (UAX #29 + #11)
- **toml-rs** (Rust): TOML 1.0.0 parser
- **uid-py** and **uid-js**: ULID + UUIDv7 for Python and Node
- **jsonheal-py**: repair almost-JSON text into valid JSON
- **sse-py**: Server-Sent Events parser
- **patch-py**: apply and produce unified diffs
- **pwhash-py**: password hashing (scrypt)
- **otp-py**: TOTP / HOTP one-time passwords
- **jwt-hs-py**: HMAC-signed JWTs
- **agtop** (Rust): htop for coding agents, a live terminal monitor
- **fp-py** and **fp-js**: lightweight fingerprinting
- **web-server-rs** and **web-server-py**: a lightweight, zero-dependency web server

## How every package is built

```bash
python dev.py check   # dependency guard + formatting + tests (the pre-push gate)
```

`dev.py` is pure standard-library Python, so the same one command works
identically across the Rust, Python, and JavaScript packages. The dependency
guard is the heart of it: it fails the build if a package ever declares a
third-party dependency.

## Want to help?

nativelite is young and contributions are genuinely welcome, whether that is a bug
report, a new package idea, a port of an existing one to another language, or a
fix. If any of this resonates and you want to help, please reach out: open an
issue or a discussion on the relevant repo, or get in touch with
[@JSBtechnologies](https://github.com/JSBtechnologies). No contribution is too
small, and no question is a bad one.

---

MIT licensed, built in the open.
