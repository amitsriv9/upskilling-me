# 6-Week Plan to Learn Go

**Assumptions:** You already program in another language, and you can spend about 6-8 hours per week. The plan favors writing code over reading about it, and it ends with a deployable project.

---

## Week 1: Language Basics

**Goal:** Get comfortable with Go's syntax and tooling.

- Install Go, set up modules (`go mod init`), and learn the core commands: `go run`, `go build`, `go test`, `go fmt`, `go vet`
- Variables, constants, basic types, control flow (`if`, `for`, `switch`; Go has only one loop keyword)
- Functions, multiple return values, and named returns
- Arrays, slices, and maps, with particular attention to how slices work internally (length, capacity, shared backing arrays)
- Resource: *A Tour of Go* (go.dev/tour), then *Go by Example*

**Practice:** Solve 10-15 small problems (word counter, FizzBuzz variants, simple CLI calculator).

---

## Week 2: Types, Structs, and Interfaces

**Goal:** Learn how Go models data and behavior without classes.

- Structs, methods, and value vs. pointer receivers
- Pointers (simpler than in C, but essential)
- Interfaces and implicit satisfaction, plus the empty interface and type assertions
- Composition via struct embedding instead of inheritance
- Error handling: the `error` interface, `if err != nil`, wrapping with `fmt.Errorf("%w")`, `errors.Is` and `errors.As`
- Packages, exported vs. unexported names, and project layout

**Mini-project:** A command-line todo app that stores tasks in a JSON file, using structs, interfaces for storage, and proper error handling.

---

## Week 3: Concurrency

**Goal:** Understand what makes Go distinctive.

- Goroutines and the `sync.WaitGroup`
- Channels (buffered and unbuffered), `select`, and closing channels
- `sync.Mutex`, `sync.RWMutex`, and `sync/atomic`
- The `context` package for cancellation and timeouts
- Common patterns: worker pools, fan-out/fan-in, pipelines
- Race conditions and the `-race` flag
- Resource: *Concurrency in Go* (Katherine Cox-Buday), selected chapters; Go blog posts on pipelines and context

**Mini-project:** A concurrent web link checker that fetches many URLs with a worker pool, a timeout, and cancellation.

---

## Week 4: Standard Library and Testing

**Goal:** Learn to be productive with the standard library before reaching for third-party packages.

- `io`, `bufio`, `os`, `strings`, `encoding/json`, `time`
- `net/http`: building a server, handlers, middleware, and an HTTP client
- Logging with `log/slog`
- Testing: table-driven tests, subtests, `testing` helpers, benchmarks, `httptest`
- Code coverage and `go test -cover`
- Generics (type parameters and constraints), used sparingly and where they help

**Practice:** Add a full test suite to your Week 2 or Week 3 project, including at least one benchmark.

---

## Week 5: Building a Real Service

**Goal:** Put the pieces together in a realistic backend.

- REST API design with `net/http` (and optionally a router such as chi)
- Working with a database: `database/sql` with Postgres or SQLite, migrations, and connection pooling
- Configuration via environment variables, graceful shutdown, and structured logging
- Project structure (`cmd/`, `internal/`), dependency injection through interfaces
- Dockerizing a Go app with a multi-stage build

**Project (start):** Build a REST API (for example a bookmarks or notes service) with CRUD endpoints, persistence, validation, and tests.

---

## Week 6: Polish, Tooling, and Idiomatic Go

**Goal:** Finish the project and write code that looks like Go.

- Finish and deploy the Week 5 project (Docker plus any simple host)
- Linting with `golangci-lint`, plus `go vet` and `staticcheck`
- Profiling with `pprof` and reading benchmark results
- Idioms: accept interfaces and return structs, keep interfaces small, avoid premature abstraction, handle errors explicitly
- Read well-regarded Go code (parts of the standard library, or a project like Caddy)
- Resource: *Effective Go*, *Go Code Review Comments*, *100 Go Mistakes and How to Avoid Them* (Teiva Harsanyi)

**Final deliverable:** A deployed, tested, documented service with a README covering setup, endpoints, and design decisions.

---

## Topics to Study Further for Depth

| Area | Why it matters |
|---|---|
| **Advanced concurrency** | Memory model, `errgroup`, rate limiting, avoiding goroutine leaks |
| **Performance tuning** | Escape analysis, allocations, garbage collector behavior, `pprof` and `trace` |
| **gRPC and Protocol Buffers** | Common for service-to-service communication in Go shops |
| **Observability** | OpenTelemetry, Prometheus metrics, distributed tracing |
| **Cloud-native Go** | Kubernetes client-go, writing operators and CLIs with Cobra |
| **Advanced generics and reflection** | Library design and understanding how frameworks work |
| **Database patterns** | `sqlc`, transactions, query optimization, testing against real databases |

---

## Tips for Making It Stick

1. **Type the code yourself.** Avoid copy-paste; Go's small syntax rewards repetition.
2. **Embrace the simplicity.** If you're reaching for clever abstractions, you're probably fighting the language.
3. **Run `go fmt` and `go vet` constantly.** They are part of the culture and catch many mistakes early.
4. **Always test with `-race`** once you start using goroutines.
5. **Read the standard library source.** It's readable and a great model of idiomatic Go.