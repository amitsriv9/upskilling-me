# 6-Week Go Plan for a Python Developer Building Scalable Services

You already have the hard part (programming fundamentals, HTTP, databases), so this plan skips the basics and focuses on where Go differs from Python and on what scalable services need.

## Python-to-Go mental shifts to expect

| Python habit | Go reality |
|---|---|
| Exceptions | Errors are return values (`if err != nil`), with no try/except |
| Classes and inheritance | Structs, methods, composition, and small implicit interfaces |
| Duck typing | Static typing, but interfaces are satisfied implicitly, so it feels familiar |
| `asyncio` / threads and the GIL | Goroutines and channels give true parallelism with no `async/await` coloring |
| Dynamic dicts and lists | Typed slices and maps, where slice capacity and aliasing cause surprises |
| `None` and truthiness | Zero values (`0`, `""`, `nil`) and no implicit truthiness |
| Decorators and metaprogramming | Plain functions, middleware wrappers, and little magic |
| Virtualenv and pip | Modules (`go.mod`) and a single static binary |

---

## Week 1: Core Language, Fast

- Tooling: `go mod`, `go run/build/test`, `go fmt`, `go vet`
- Types, zero values, control flow, multiple returns, `defer`
- Slices (length vs. capacity, shared backing arrays), maps, strings and runes
- Pointers and when to use them
- Resource: *A Tour of Go*, then *Go by Example*

**Practice:** Port 5-6 small Python scripts you've written before into Go (log parser, CSV processor, CLI tool).

## Week 2: Structs, Interfaces, and Errors

- Structs, value vs. pointer receivers, embedding
- Interfaces: define them at the consumer, keep them small
- Error handling idioms: wrapping with `%w`, `errors.Is/As`, sentinel and custom errors
- Packages and project layout (`cmd/`, `internal/`)
- Generics basics

**Mini-project:** A CLI tool with a pluggable storage interface (file and in-memory implementations) and thorough tests.

## Week 3: Concurrency (the Core of Scalability)

- Goroutines, channels, `select`, `sync.WaitGroup`, `Mutex`
- `context` for cancellation, deadlines, and request-scoped values
- Patterns: worker pools, pipelines, fan-out/fan-in, `errgroup`
- Avoiding goroutine leaks and data races (`go test -race`)
- Contrast with `asyncio`: no event-loop coloring, but you manage lifetimes yourself

**Mini-project:** A concurrent crawler or batch processor with bounded concurrency, timeouts, and clean cancellation.

## Week 4: HTTP Services and the Standard Library

- `net/http` server, handlers, middleware chains (logging, recovery, auth, request IDs)
- JSON encoding, validation, and consistent error responses
- Structured logging with `log/slog`
- Testing with `httptest`, table-driven tests, and benchmarks
- Router choice: stdlib `ServeMux` (modern versions support method and path patterns) or chi

**Project (start):** A REST API (for example, a URL shortener or task service) with clean layering: handler, service, repository.

## Week 5: Production Concerns

- Database access: `database/sql` with `pgx` (or `sqlc` for type-safe queries), connection pooling, transactions, migrations
- Caching with Redis, and idempotency and retries with backoff
- Rate limiting and timeouts on every outbound call
- Config via environment variables, graceful shutdown, health and readiness endpoints
- Observability: Prometheus metrics, OpenTelemetry tracing, structured logs
- Docker multi-stage builds (small static images)

**Project (continue):** Add Postgres, Redis caching, metrics, tracing, and graceful shutdown to your service.

## Week 6: Scale, Performance, and Deployment

- Load test your service (k6, vegeta, or hey) and find bottlenecks
- Profile with `pprof` (CPU, heap, goroutines) and read benchmark output
- Understand allocations, escape analysis basics, and `sync.Pool` where warranted
- Intro to gRPC and Protocol Buffers for service-to-service calls
- Deploy to Kubernetes or a container platform with resource limits and horizontal scaling
- Idiom polish: *Effective Go*, *Go Code Review Comments*, *100 Go Mistakes* (Teiva Harsanyi)

**Final deliverable:** A deployed, load-tested, observable service with a README covering architecture, benchmarks before and after tuning, and tradeoffs.

---

## Topics to Study Further for Depth

| Area | Why it matters for scalable services |
|---|---|
| **Advanced concurrency** | Memory model, backpressure, avoiding leaks and contention |
| **gRPC and service meshes** | Efficient internal communication, streaming, load balancing |
| **Messaging and event-driven design** | Kafka, NATS, or RabbitMQ for decoupling and throughput |
| **Distributed systems fundamentals** | Consistency, retries, idempotency, circuit breakers, sagas |
| **Database scaling** | Indexing, replicas, partitioning, query tuning |
| **Garbage collector and memory tuning** | `GOGC`, `GOMEMLIMIT`, reducing allocations in hot paths |
| **Kubernetes and cloud-native Go** | Autoscaling, operators, `client-go` |
| **Resilience and testing in production** | Chaos testing, canary deploys, SLOs and error budgets |

---

## Python-Specific Tips

1. **Resist writing Python in Go.** Skip clever abstractions and deep class-like hierarchies. Flat, explicit code is idiomatic.
2. **Pass `context.Context` everywhere** as the first parameter of anything that does I/O. It's the backbone of scalable service behavior.
3. **Bound everything**: goroutines, queue sizes, connection pools, and timeouts. Unbounded concurrency is the most common scaling mistake.
4. **Benchmark before optimizing.** Go is fast by default, so most gains come from architecture and I/O, not micro-tuning.
5. **Keep your Python strengths** (testing discipline, API design, readability) and apply them with Go's conventions.