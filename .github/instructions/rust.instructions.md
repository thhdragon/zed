## Core Workflow

1. **Understand the Problem**
   - Read the issue carefully
   - Identify expected behavior and edge cases
   - Consider dependencies and interactions

2. **Investigate Codebase**
   - Explore relevant files (`mod.rs`, `lib.rs`, etc.)
   - Search for key `fn`, `struct`, `enum`, `trait` items
   - Use `cargo tree`, `cargo-expand`, `cargo doc --open`

3. **Research** 
   - Search Stack Overflow, [docs.rs](https://docs.rs), [users.rust-lang.org](https://users.rust-lang.org)
   - Verify third-party crate usage patterns

4. **Plan & Execute**
   - Create markdown todo list: `- [ ] Task description`
   - Mark completed: `- [x] Task description`
   - Make small, testable changes
   - Test frequently with `cargo test`, `cargo build`, `cargo run`

## Rust-Specific Guidelines

### HTTP Requests
- Use `reqwest`, `ureq`, or `surf`
- Handle `Result` types properly
- Use `async`/`await` with `tokio` or `async-std`

### Code Quality
- Use `cargo fmt`, `cargo clippy`
- Avoid `.unwrap()` - use proper error handling
- Prefer borrowing over `.clone()`
- Don't optimize prematurely

### Debugging
- Use `dbg!()` macro for temporary logging
- Use `tracing` or `log` crates for proper logging
- Set `RUST_BACKTRACE=1` for stack traces
- Use `cargo-expand` to debug macros

### GUI Safety (if applicable)
- GUI must run on main thread
- Use `glib::Sender` or `glib::idle_add_local()` for thread communication
- Handle reference counting with `Rc`, `Arc`, `Weak`
- Use `Arc<Mutex<T>>` for shared state across threads

### Avoid Anti-Patterns
- Unnecessary `.clone()` calls
- Overusing `.unwrap()`/`.expect()`
- Early `.collect()` calls
- Unsafe code without clear need
- Over-abstraction with traits/generics
- Global mutable state
- Heavy macro usage