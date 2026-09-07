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
   safe FFI when needed), nothing else. A dependency guard enforces it in every
   package.
2. **One concern per package.** A package does exactly one thing well. If it grows
   a second concern, that concern becomes its own package.
3. **Correctness first, then performance, then ergonomics**, in that order. A fast
   wrong answer is a bug. We benchmark and we prove.
4. **Spec-anchored tests.** Correctness is anchored to the spec (RFC 8259,
   RFC 6238, UAX #29, and so on), not just to round-trips.
5. **Small surface, honest docs.** The README never claims what the code does not
   do. Examples are runnable and tested.

## Packages

### IDs and time

- **[uid-rs](https://github.com/nativelite/uid-rs)**: ULID + UUIDv7 on Rust std
- **[uid-py](https://github.com/nativelite/uid-py)**: ULID + UUIDv7 on Python std
- **[uid-js](https://github.com/nativelite/uid-js)**: ULID + UUIDv7 on Node std
- **[duration](https://github.com/nativelite/duration)**: parse and format human durations to and from milliseconds

### Parsing and data

- **[json-rs](https://github.com/nativelite/json-rs)**: RFC 8259 JSON parser and serializer (Rust std only)
- **[jsonheal-py](https://github.com/nativelite/jsonheal-py)**: repair almost-JSON text into valid JSON (Python std only)
- **[toml-rs](https://github.com/nativelite/toml-rs)**: TOML 1.0.0 parser (Rust std only)
- **[sse-py](https://github.com/nativelite/sse-py)**: Server-Sent Events parser (Python std only)
- **[patch-py](https://github.com/nativelite/patch-py)**: apply and produce unified diffs (Python std only)

### Terminal, TUI, and agents

- **[ansi-rs](https://github.com/nativelite/ansi-rs)**: ANSI/VT terminal output as data (Rust std only)
- **[rawterm-rs](https://github.com/nativelite/rawterm-rs)**: raw terminal mode and key/resize events via OS FFI (Rust std only)
- **[pty-rs](https://github.com/nativelite/pty-rs)**: spawn a child on a real pseudo-terminal (Rust std only)
- **[vterm-rs](https://github.com/nativelite/vterm-rs)**: a minimal terminal-emulator core (Rust std only)
- **[uwidth](https://github.com/nativelite/uwidth)**: grapheme-correct terminal text measurement (UAX #29 + #11)
- **[agsess](https://github.com/nativelite/agsess)**: local agent session state, read from coding-agent transcripts
- **[agtop](https://github.com/nativelite/agtop)**: htop for coding agents, a live terminal monitor
- **[atrium](https://github.com/nativelite/atrium)**: tmux for coding agents, a multi-agent terminal

### Security and secrets

- **[pwhash-py](https://github.com/nativelite/pwhash-py)**: password hashing (scrypt, Python std only)
- **[otp-py](https://github.com/nativelite/otp-py)**: TOTP / HOTP one-time passwords (Python std only)
- **[jwt-hs-py](https://github.com/nativelite/jwt-hs-py)**: HMAC-signed JWTs (Python std only)
- **[cred-rs](https://github.com/nativelite/cred-rs)**: named secrets in the OS credential vault (Rust std + FFI)
- **[akey](https://github.com/nativelite/akey)**: API keys and Workload Identity Federation profiles for agent tooling

### Web and other

- **[fp-js](https://github.com/nativelite/fp-js)**: lightweight browser fingerprinting
- **[fp-py](https://github.com/nativelite/fp-py)**: lightweight device fingerprinting
- **[web-server-rs](https://github.com/nativelite/web-server-rs)**: a lightweight web server, zero external libraries (coming soon)
- **[web-server-py](https://github.com/nativelite/web-server-py)**: a lightweight web server, zero external libraries (coming soon)

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
