# Comprehensive Code Analysis Prompt

A Claude Code prompt template for generating detailed codebase metrics reports with interactive HTML dashboards and PDF export.

[![GitHub](https://img.shields.io/badge/GitHub-d--e--v--com%2FAi--prompts-blue?logo=github)](https://github.com/d-e-v-com/Ai-prompts)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Features

- **14 Metric Categories** - Code quality, complexity, coupling, OO metrics, design patterns, security, testing, and more
- **AWS Well-Architected Framework** - Six-pillar alignment scoring
- **DocOps Assessment** - Installation, repeatability, operational documentation scoring
- **Interactive Dashboard** - Chart.js visualizations with dark/light mode
- **PDF Export** - One-click PDF generation for sharing
- **Industry Standards** - Based on SOLID, SQALE, CK Metrics, and more

---

## KPI Metrics & Industry Benchmarks

This tool analyzes **14 metric categories** and scores them against industry benchmarks:

### Core Code Quality Metrics

| # | Metric Category | Key KPIs | Benchmark (Good) |
|---|----------------|----------|------------------|
| 1 | **Code Quality Fundamentals** | SLOC, Cyclomatic Complexity, Cognitive Complexity, Maintainability Index, Comment Ratio, Duplication % | Complexity < 10, Maintainability > 65 |
| 2 | **Call Stack & Coupling** | Max Call Depth, Blast Radius, Files Per Change, Coupling Score, Instability Index | Depth < 10, Files/Change < 5 |
| 3 | **CK Metrics (Chidamber-Kemerer)** | WMC, DIT, NOC, CBO, RFC, LCOM | WMC < 50, CBO < 14, LCOM < 0.5 |
| 4 | **MOOD Metrics** | MHF, AHF, MIF, AIF, PF, CF | MHF > 0.5, AHF > 0.8, CF < 0.2 |
| 5 | **Design Pattern Detection** | Creational, Structural, Behavioral, Architectural patterns | Patterns detected with confidence scores |
| 6 | **Anti-Pattern Detection** | God Class, Spaghetti Code, Feature Envy, Circular Dependencies, 30+ anti-patterns | 0 critical anti-patterns |
| 7 | **SOLID Compliance** | Single Responsibility, Open/Closed, Liskov, Interface Segregation, Dependency Inversion | Score > 70 per principle |

### Security, Testing & Documentation

| # | Metric Category | Key KPIs | Benchmark (Good) |
|---|----------------|----------|------------------|
| 8 | **Security Metrics** | OWASP Top 10, Secrets Detection, SQL Injection, XSS, Encryption Coverage | 0 critical vulnerabilities |
| 9 | **Test Quality Metrics** | Line Coverage, Branch Coverage, Mutation Score, Test-to-Code Ratio, Assertion Density | Coverage > 80%, Ratio 0.5-1.5 |
| 10 | **Documentation Metrics** | Public API Docs, README Score, Changelog, Architecture Docs | API Docs > 90% |
| 11 | **Technical Debt (SQALE)** | Debt Ratio, Remediation Time, Debt by Category, Hotspots | Debt Ratio < 5% |

### Operational Readiness

| # | Metric Category | Key KPIs | Benchmark (Good) |
|---|----------------|----------|------------------|
| 12 | **DocOps Assessment** | Installation Docs, Repeatability, Operational Docs, Troubleshooting | Score > 70 |
| 13 | **AWS Well-Architected** | Operational Excellence, Security, Reliability, Performance, Cost Optimization, Sustainability | Score > 70 per pillar |
| 14 | **Code Churn & Evolution** | Churn Rate, Hotspot Files, Author Concentration, Change Coupling | Bus Factor > 2 |

### Industry Benchmark Thresholds

| Metric | Poor | Fair | Good | Excellent |
|--------|------|------|------|-----------|
| Maintainability Index | < 40 | 40-65 | 65-85 | > 85 |
| Cyclomatic Complexity (avg) | > 15 | 10-15 | 5-10 | < 5 |
| Cognitive Complexity (avg) | > 20 | 15-20 | 8-15 | < 8 |
| Technical Debt Ratio | > 20% | 10-20% | 5-10% | < 5% |
| Test Coverage | < 40% | 40-60% | 60-80% | > 80% |
| Duplication | > 10% | 5-10% | 3-5% | < 3% |
| LCOM (Cohesion) | > 0.8 | 0.5-0.8 | 0.3-0.5 | < 0.3 |
| Coupling (CBO avg) | > 20 | 14-20 | 8-14 | < 8 |
| Call Stack Depth (max) | > 15 | 10-15 | 5-10 | < 5 |
| Files Per Change | > 10 | 5-10 | 3-5 | < 3 |
| Circular Dependencies | > 5 | 2-5 | 1-2 | 0 |
| SOLID Score | < 40 | 40-60 | 60-80 | > 80 |
| DocOps Score | < 40 | 40-60 | 60-80 | > 80 |
| Well-Architected Score | < 40 | 40-60 | 60-80 | > 80 |
| Security Posture | Critical gaps | Some gaps | Good | Defense in depth |

---

## Quick Start

### Prerequisites
- [Claude Code CLI](https://claude.ai/code) installed and configured

### Usage

1. **Install Claude Code** - Follow instructions at [claude.ai/code](https://claude.ai/code)

2. **Login to your terminal and start Claude:**
   ```bash
   claude
   ```

3. **Enter the following prompt:**
   ```
   load and execute the CLAUDE_CODE_REVIEW.md procedures on the following project code base: /path/to/your/code
   ```

4. **Watch the magic happen!** The tool will analyze your codebase and generate an interactive report.

5. **View the generated report:**
   - Open `output-reports/YYYY-MM-DD_projectName_code_review_report/index.html` in your browser
   - Click **📄 Export PDF** button to generate a shareable PDF
   - Review `data.json` for raw metrics data

Enjoy! =]

### Output Structure
```
output-reports/
└── YYYY-MM-DD_codebaseName_code_review_report/
    ├── data.json                                              # Raw metrics data (JSON)
    ├── index.html                                             # Interactive dashboard
    ├── YYYY-MM-DD_codebaseName_ACTION_ITEMS.md                # Remediation plan (Markdown)
    ├── YYYY-MM-DD_codebaseName_ACTION_ITEMS.html              # Remediation plan (HTML)
    ├── YYYY-MM-DD_codebaseName_ACTION_ITEMS.pdf               # Remediation plan (PDF) - auto-generated
    ├── YYYY-MM-DD_codebaseName_CODE_REVIEW_AUDIT_REPORT.png   # Dashboard screenshot - auto-generated
    └── YYYY-MM-DD_codebaseName_CODE_REVIEW_AUDIT_REPORT.pdf   # Dashboard PDF - auto-generated
```
**Note:** All 7 files are generated automatically. PDF and PNG files are created via headless browser.

### Example
```bash
# Analyzing a project called "my-api"
cd ~/projects/my-api
mkdir -p output-reports/$(date +%Y-%m-%d)_my-api_code_review_report

# Run Claude Code and use the prompt below
claude
```

### Sample Report

Here's what to expect from the generated report:

| Section | Description |
|---------|-------------|
| **Overall Health** | Grade A-F with key metrics (SLOC, complexity, maintainability) |
| **Security Score** | Vulnerability breakdown with severity levels |
| **SOLID Compliance** | Radar chart showing principle adherence |
| **Well-Architected** | Six-pillar radar with current vs target scores |
| **DocOps Score** | Documentation completeness assessment |
| **Anti-Patterns** | Detected code smells with locations |
| **High Risk Files** | Table of files needing attention |
| **Recommendations** | Prioritized action items (immediate/short/long term) |

---

## The Analysis Prompt

Copy everything between the triple backticks below and paste into Claude Code:

```
Analyze this project's codebase and generate a comprehensive metrics report following industry standards.

Save all output files to: output-reports/YYYY-MM-DD_CODEBASE-NAME_code_review_report/
(Replace YYYY-MM-DD with today's date and CODEBASE-NAME with the project name)

Create the following files:
1. `data.json` - Raw metrics data
2. `index.html` - Interactive dashboard with PDF/PNG export
3. `YYYY-MM-DD_CODEBASE-NAME_ACTION_ITEMS.md` - Actionable remediation plan with Epics, Stories, and Subtasks
4. `YYYY-MM-DD_CODEBASE-NAME_ACTION_ITEMS.html` - Styled HTML version of action items (for PDF generation)
5. `YYYY-MM-DD_CODEBASE-NAME_ACTION_ITEMS.pdf` - PDF export of action items (executive-friendly for email sharing)
6. `YYYY-MM-DD_CODEBASE-NAME_CODE_REVIEW_AUDIT_REPORT.png` - Full-page PNG screenshot of dashboard
7. `YYYY-MM-DD_CODEBASE-NAME_CODE_REVIEW_AUDIT_REPORT.pdf` - PDF export of dashboard

## Metrics to Calculate

### 1. Code Quality Fundamentals (per file and aggregate)

| Metric | Description | Target |
|--------|-------------|--------|
| **SLOC** | Source lines of code, excluding blanks and comments | Context-dependent |
| **Cyclomatic Complexity** | Decision points (if, else, switch, for, while, catch, &&, \|\|, ternary, pattern matching) | < 10 per method |
| **Cognitive Complexity** | SonarQube standard - weighted complexity accounting for nesting depth and breaks in linear flow | < 15 per method |
| **Maintainability Index** | `171 - 5.2*ln(Halstead Volume) - 0.23*(Cyclomatic Complexity) - 16.2*ln(SLOC)`, scaled 0-100 | > 65 |
| **Comment Ratio** | Comments per 100 lines of code | 10-20% |
| **Duplication %** | Percentage of duplicated code blocks (6+ consecutive similar lines) | < 5% |

### 2. Call Stack & Coupling Analysis (NEW)

#### Call Stack Depth
| Metric | Description | Target |
|--------|-------------|--------|
| **Max Call Depth** | Deepest synchronous call chain from entry point | < 10 |
| **Average Call Depth** | Mean depth across all execution paths | < 5 |
| **Recursive Depth** | Maximum recursion depth detected | < 5 |
| **Async Chain Length** | Promise/await/callback chain depth | < 5 |

#### Change Impact Analysis
| Metric | Description | Target |
|--------|-------------|--------|
| **Files Per Change** | Estimated files touched for typical change (via coupling analysis) | < 5 |
| **APIs Per Change** | Number of interfaces/contracts affected by single change | < 3 |
| **Blast Radius** | Transitive dependencies affected by changing a file | < 20 files |
| **Coupling Score** | Fan-in × Fan-out for each module | < 100 |
| **Instability Index** | Fan-out / (Fan-in + Fan-out) - higher = more likely to change | 0-1 |
| **Abstractness** | Abstract classes & interfaces / Total classes | 0-1 |
| **Distance from Main Sequence** | |Abstractness + Instability - 1| - should be near 0 | < 0.3 |

#### Dependency Metrics
| Metric | Description | Target |
|--------|-------------|--------|
| **Afferent Coupling (Ca)** | Incoming dependencies (who depends on me) | Monitor |
| **Efferent Coupling (Ce)** | Outgoing dependencies (who do I depend on) | < 20 |
| **Dependency Depth** | Longest path in dependency graph | < 6 |
| **Circular Dependencies** | Bidirectional dependency cycles | 0 |
| **Hub Files** | Files with both high Ca and Ce (fragile connectors) | Flag for review |

### 3. Object-Oriented Metrics (MOOD & CK Metrics)

#### Chidamber & Kemerer (CK) Metrics
| Metric | Description | Target |
|--------|-------------|--------|
| **WMC** | Weighted Methods per Class - sum of complexity | < 50 |
| **DIT** | Depth of Inheritance Tree | < 5 |
| **NOC** | Number of Children (subclasses) | Context-dependent |
| **CBO** | Coupling Between Objects | < 14 |
| **RFC** | Response For Class - methods + called methods | < 50 |
| **LCOM** | Lack of Cohesion in Methods (0 = cohesive, 1 = no cohesion) | < 0.5 |
| **LCOM4** | Improved LCOM - connected components in method graph | 1 (ideal) |

#### MOOD Metrics (Metrics for Object-Oriented Design)
| Metric | Description | Target |
|--------|-------------|--------|
| **MHF** | Method Hiding Factor - encapsulation of methods | > 0.5 |
| **AHF** | Attribute Hiding Factor - encapsulation of fields | > 0.8 |
| **MIF** | Method Inheritance Factor | 0.2-0.8 |
| **AIF** | Attribute Inheritance Factor | 0.2-0.8 |
| **PF** | Polymorphism Factor | Context-dependent |
| **CF** | Coupling Factor | < 0.2 |

### 4. Design Pattern Detection

#### Creational Patterns
| Pattern | Detection Signals |
|---------|-------------------|
| **Singleton** | Private constructor, static instance, getInstance() method |
| **Factory Method** | Abstract creator, concrete creators returning product interface |
| **Abstract Factory** | Family of factory methods, related product interfaces |
| **Builder** | Fluent interface, step-by-step construction, build() method |
| **Prototype** | Clone/copy methods, Cloneable interface |
| **Object Pool** | Acquire/release methods, collection of reusable instances |
| **Dependency Injection** | Constructor injection, @Inject/@Autowired annotations |

#### Structural Patterns
| Pattern | Detection Signals |
|---------|-------------------|
| **Adapter** | Implements target interface, wraps adaptee |
| **Bridge** | Abstraction with implementor reference, separate hierarchies |
| **Composite** | Component interface, leaf and composite implementing same interface |
| **Decorator** | Wraps component, implements same interface, adds behavior |
| **Facade** | Simplified interface to complex subsystem |
| **Flyweight** | Factory returning shared instances, intrinsic/extrinsic state |
| **Proxy** | Same interface as subject, controls access |
| **Module** | Namespace encapsulation, public API exposure |

#### Behavioral Patterns
| Pattern | Detection Signals |
|---------|-------------------|
| **Chain of Responsibility** | Handler interface, next handler reference |
| **Command** | Execute method, command objects, invoker/receiver |
| **Iterator** | hasNext/next methods, Iterable implementation |
| **Mediator** | Central coordinator, colleagues communicate through mediator |
| **Memento** | State capture/restore, caretaker managing mementos |
| **Observer** | Subscribe/notify methods, listener collections |
| **State** | State interface, context delegating to state object |
| **Strategy** | Algorithm interface, interchangeable implementations |
| **Template Method** | Abstract class with final template, abstract steps |
| **Visitor** | Accept method, visitor with visit methods per type |
| **Specification** | IsSatisfiedBy method, combinable predicates |

#### Architectural Patterns
| Pattern | Detection Signals |
|---------|-------------------|
| **MVC** | Model/View/Controller separation, update notifications |
| **MVP** | Presenter mediating between Model and passive View |
| **MVVM** | ViewModel with observable properties, data binding |
| **Repository** | Data access abstraction, collection-like interface |
| **Unit of Work** | Transaction tracking, commit/rollback |
| **CQRS** | Separate command and query models |
| **Event Sourcing** | Event store, state from event replay |
| **Hexagonal/Ports & Adapters** | Core domain, port interfaces, adapter implementations |
| **Clean Architecture** | Dependency rule, use cases, entities |
| **Domain-Driven Design** | Aggregates, entities, value objects, domain events |

#### Anti-Pattern Detection (Design Smells)
| Anti-Pattern | Detection |
|--------------|-----------|
| **God Class** | WMC > 50, LCOM > 0.8, 20+ methods or 1000+ lines |
| **Blob/Monster** | Single class doing everything, low cohesion |
| **Spaghetti Code** | High complexity, no clear structure, goto-like jumps |
| **Golden Hammer** | One pattern used everywhere inappropriately |
| **Lava Flow** | Dead code, unused classes, orphaned methods |
| **Poltergeist** | Short-lived classes that just invoke others |
| **Boat Anchor** | Unused code kept "just in case" |
| **Dead End** | Classes with no subclasses in inheritance hierarchies |
| **Circular Dependency** | A→B→C→A dependency cycles |
| **Feature Envy** | Method using other class's data more than its own |
| **Data Clumps** | Same group of fields appearing together repeatedly |
| **Primitive Obsession** | Overuse of primitives instead of small objects |
| **Parallel Inheritance** | Every subclass in A requires subclass in B |
| **Speculative Generality** | Abstract classes with single implementation |
| **Refused Bequest** | Subclass not using inherited methods |
| **Inappropriate Intimacy** | Excessive access to another class's internals |
| **Message Chains** | a.getB().getC().getD() chains |
| **Middle Man** | Class delegating most work elsewhere |
| **Divergent Change** | One class changed for multiple unrelated reasons |
| **Shotgun Surgery** | One change requires edits across many classes |

### 5. SOLID Principles Compliance

| Principle | Detection Method | Scoring |
|-----------|-----------------|---------|
| **S - Single Responsibility** | LCOM score, method clustering, class description complexity | 0-100 |
| **O - Open/Closed** | Extension points, inheritance usage, modification history | 0-100 |
| **L - Liskov Substitution** | Override behavior analysis, precondition/postcondition changes | 0-100 |
| **I - Interface Segregation** | Interface size, client usage patterns, unused method implementations | 0-100 |
| **D - Dependency Inversion** | Concrete vs abstract dependencies, injection patterns | 0-100 |

### 6. Language-Specific Anti-Patterns

#### PHP
| Pattern | Detection |
|---------|-----------|
| Magic array keys | `#`-prefixed array keys like `$form['#attributes']` |
| Deep array nesting | 3+ levels of array depth |
| Service locators | `\Drupal::service()`, `Container::get()` calls |
| God classes | Classes with 20+ methods or 500+ lines |
| Suppressed errors | `@` error suppression operator |
| Mixed concerns | HTML/SQL/business logic in same file |
| Global state | Global variables, superglobal abuse |

#### JavaScript/TypeScript
| Pattern | Detection |
|---------|-----------|
| Callback hell | 3+ nested callbacks |
| Any type abuse | `any` type in TypeScript files |
| Console statements | `console.log/warn/error` in production code |
| Magic strings | Repeated string literals (3+ occurrences) |
| Prototype pollution | Direct `__proto__` or `prototype` manipulation |
| Missing null checks | Optional chaining candidates |
| Event listener leaks | addEventListener without removeEventListener |
| Implicit globals | Variables without declaration |
| this binding issues | Unbound this in callbacks |
| Synchronous XHR | Blocking HTTP calls |

#### Python
| Pattern | Detection |
|---------|-----------|
| Bare except | `except:` without exception type |
| Mutable defaults | `def func(arg=[])` or `def func(arg={})` |
| Global variables | `global` keyword usage |
| Star imports | `from module import *` |
| Deep nesting | 4+ indentation levels |
| Magic numbers | Numeric literals without constants |
| Type hint gaps | Missing type hints on public APIs |
| Circular imports | Import cycles between modules |
| Assert in production | Using assert for validation |
| Hardcoded paths | Absolute file paths in code |

#### Java
| Pattern | Detection |
|---------|-----------|
| God classes | Classes with 20+ methods or 1000+ lines |
| Long methods | Methods exceeding 50 lines |
| Deep inheritance | Inheritance depth > 4 levels |
| Catch-all exceptions | `catch (Exception e)` or `catch (Throwable t)` |
| Field injection | `@Autowired` on fields instead of constructor |
| Service locators | `ApplicationContext.getBean()` calls |
| Magic numbers | Numeric literals without constants |
| Null returns | Methods returning null instead of Optional |
| Public fields | Non-final public instance fields |
| Empty catch blocks | `catch` blocks with no handling |
| String concatenation in loops | `+=` on strings inside loops |
| Raw types | Generic types used without parameters |
| Checked exception abuse | Excessive checked exceptions |
| Utility class instantiation | Utility classes without private constructor |
| Mutable statics | Non-final static fields |
| Double-checked locking | Broken singleton pattern |
| Finalizer usage | finalize() method overrides |

#### C# / .NET
| Pattern | Detection |
|---------|-----------|
| God classes | Classes with 20+ methods or 1000+ lines |
| Long methods | Methods exceeding 50 lines |
| Deep inheritance | Inheritance depth > 4 levels |
| Catch-all exceptions | `catch (Exception)` without specific types |
| Service locators | `ServiceLocator.Current`, `IServiceProvider` direct calls |
| Magic numbers | Numeric literals without constants |
| Async void | `async void` methods (except event handlers) |
| Disposable not disposed | `IDisposable` without `using` or `Dispose()` |
| Public fields | Non-readonly public instance fields |
| Empty catch blocks | `catch` blocks with no handling |
| String concatenation in loops | `+=` on strings inside loops |
| Regions abuse | Excessive `#region` blocks (10+ per file) |
| Dynamic abuse | Overuse of `dynamic` keyword |
| CA violations | Common Code Analysis rule violations |
| ConfigureAwait missing | Library code without ConfigureAwait(false) |
| Event handler leaks | Event subscriptions without unsubscription |
| Virtual in constructor | Calling virtual methods in constructors |
| ICloneable implementation | Implementing problematic ICloneable |

#### Go
| Pattern | Detection |
|---------|-----------|
| Naked returns | Return statements without values in named return functions |
| Ignored errors | `_` for error returns |
| Global state | Package-level mutable variables |
| Init function abuse | Complex init() functions |
| Interface pollution | Interfaces defined by implementer not consumer |
| Goroutine leaks | Unbounded goroutine creation |
| Channel misuse | Unbuffered channels causing deadlocks |
| Context misuse | context.Background() in production code |
| Panic in libraries | panic() instead of returning errors |
| Magic strings | Repeated string literals |

#### Rust
| Pattern | Detection |
|---------|-----------|
| Unwrap abuse | `.unwrap()` and `.expect()` in production code |
| Clone abuse | Excessive `.clone()` calls |
| Unsafe blocks | `unsafe` block proliferation |
| Macro overuse | Complex procedural macros |
| Lifetime complexity | Excessive lifetime annotations |
| Box abuse | Unnecessary heap allocations |
| Arc<Mutex> | Could use simpler synchronization |
| Stringly typed | String instead of enums/types |

#### CloudFormation (YAML/JSON)
| Pattern | Detection |
|---------|-----------|
| Hardcoded values | Literals instead of parameters/mappings |
| Missing outputs | Stacks without `Outputs` section |
| No descriptions | Resources/parameters without `Description` |
| Overly permissive IAM | `Action: "*"` or `Resource: "*"` |
| No encryption | S3/EBS/RDS without encryption enabled |
| Public resources | S3 buckets, security groups open to 0.0.0.0/0 |
| No tags | Resources without `Tags` property |
| Long templates | Single template > 1000 lines (should be nested) |
| Missing DeletionPolicy | Stateful resources without `DeletionPolicy` |
| Default VPC usage | Resources without explicit VPC configuration |
| No condition usage | Large templates without `Conditions` |
| Missing UpdatePolicy | Auto Scaling without update policy |
| Hardcoded AZs | Availability zones hardcoded |
| No stack policies | Missing stack policy for protection |

#### Terraform (HCL)
| Pattern | Detection |
|---------|-----------|
| Hardcoded values | Literals instead of variables |
| Missing outputs | Modules without `output` blocks |
| No descriptions | Variables/outputs without `description` |
| Overly permissive IAM | `actions = ["*"]` or `resources = ["*"]` |
| No encryption | Resources without encryption arguments |
| Public resources | Security groups with 0.0.0.0/0 ingress |
| No tags | Resources without `tags` block |
| Large modules | Single module > 500 lines (should be split) |
| No lifecycle rules | Stateful resources without `lifecycle` block |
| Local-exec abuse | Overuse of `local-exec` provisioners |
| Missing provider versions | No version constraints on providers |
| No remote state | Local state file usage in team environments |
| Hardcoded ARNs | Full ARN strings instead of data sources |
| No validation | Variables without `validation` blocks |
| Count vs for_each | Using `count` where `for_each` is clearer |
| Workspace abuse | Using workspaces for environments |
| No state locking | Missing DynamoDB table for state lock |

#### Kubernetes/Helm
| Pattern | Detection |
|---------|-----------|
| Latest tag | `image: xxx:latest` |
| No resource limits | Missing CPU/memory limits |
| No health probes | Missing liveness/readiness probes |
| Root containers | Running as root user |
| No network policies | Missing network isolation |
| Hardcoded replicas | Static replica count |
| No PDB | Missing PodDisruptionBudget |
| Secrets in plain text | Unencrypted secrets |
| No RBAC | Missing role bindings |
| Privileged containers | `privileged: true` |
| Host network/PID | Using host namespaces |
| No security context | Missing securityContext |

### 7. API Surface Area

#### General (all languages)
| Category | What to count |
|----------|---------------|
| Public classes/interfaces | Exported types |
| Public methods | Methods accessible outside module |
| Configuration formats | Distinct file types (.yaml, .json, .xml, .properties) |
| External dependencies | Third-party packages/libraries |
| Entry points | Main methods, handlers, controllers |

#### PHP
| Category | Examples |
|----------|----------|
| Plugin types | Block, Field, ViewsDisplay |
| Hooks | hook_form_alter, hook_entity_presave |
| Magic keys | #theme, #states, #ajax |
| Events | KernelEvents dispatched |
| Services | Registered service definitions |

#### Java
| Category | Examples |
|----------|----------|
| Spring beans | @Component, @Service, @Repository, @Controller |
| REST endpoints | @RequestMapping, @GetMapping, @PostMapping |
| Event listeners | @EventListener, ApplicationListener implementations |
| Scheduled tasks | @Scheduled methods |
| Configuration properties | @ConfigurationProperties classes |
| Custom annotations | User-defined annotations |
| JMX beans | MBean interfaces |

#### C# / .NET
| Category | Examples |
|----------|----------|
| Controllers | ApiController, Controller classes |
| Endpoints | [HttpGet], [HttpPost], [Route] attributes |
| Middleware | IMiddleware implementations |
| Services | Registered in DI container |
| Event handlers | INotificationHandler, event delegates |
| Configuration sections | IOptions<T> bindings |
| SignalR hubs | Hub classes |
| gRPC services | Service implementations |

#### CloudFormation
| Category | Examples |
|----------|----------|
| Resource types | AWS::EC2::Instance, AWS::Lambda::Function |
| Custom resources | AWS::CloudFormation::CustomResource |
| Parameters | Input parameters defined |
| Mappings | Mapping tables defined |
| Conditions | Conditional logic defined |
| Outputs | Exported values |
| Nested stacks | AWS::CloudFormation::Stack references |
| Intrinsic functions | !Ref, !GetAtt, !Sub usage |

#### Terraform
| Category | Examples |
|----------|----------|
| Resource types | aws_instance, azurerm_virtual_machine |
| Data sources | data blocks |
| Variables | Input variables defined |
| Outputs | Output values defined |
| Modules | Module calls and definitions |
| Providers | Provider configurations |
| Locals | Local value definitions |
| Provisioners | Provisioner blocks |

### 8. Test Quality Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **Line Coverage** | % of lines executed by tests | > 80% |
| **Branch Coverage** | % of decision branches tested | > 75% |
| **Mutation Score** | % of mutants killed (if available) | > 70% |
| **Test-to-Code Ratio** | Test SLOC / Production SLOC | 0.5-1.5 |
| **Assertion Density** | Assertions per test method | > 1 |
| **Test Isolation** | Tests with external dependencies | Minimize |
| **Flaky Test Detection** | Tests with non-deterministic results | 0 |
| **Test Method Length** | Lines per test method | < 20 |
| **Test Naming** | Descriptive test names following conventions | 100% |
| **AAA Pattern** | Arrange-Act-Assert structure compliance | 100% |

### 9. Security Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **Public Exposure Score** | Count of resources exposed to internet | Minimize |
| **Encryption Coverage** | % of applicable resources with encryption | 100% |
| **IAM Least Privilege** | Inverse of wildcard permissions | > 90% |
| **Secrets in Code** | Hardcoded passwords, keys, tokens | 0 |
| **Dependency Vulnerabilities** | CVEs in dependencies | 0 critical |
| **OWASP Top 10 Coverage** | Mitigations for common vulnerabilities | 100% |
| **SQL Injection Vectors** | Unparameterized queries | 0 |
| **XSS Vectors** | Unescaped output | 0 |
| **CSRF Protection** | Forms without CSRF tokens | 0 |
| **Authentication Gaps** | Unprotected endpoints | 0 |
| **Authorization Gaps** | Missing permission checks | 0 |
| **Sensitive Data Exposure** | Logging/exposing PII | 0 |

### 10. Documentation Metrics

| Metric | Description | Target |
|--------|-------------|--------|
| **Public API Documentation** | % of public methods with docs | > 90% |
| **README Completeness** | Sections: overview, install, usage, contributing | 100% |
| **Changelog Maintenance** | Recent updates documented | Yes |
| **Architecture Docs** | ADRs, diagrams present | Yes |
| **Example Coverage** | Code examples for public APIs | > 50% |
| **Broken Links** | Invalid documentation links | 0 |
| **Outdated Docs** | Docs not matching code | 0 |

### 11. Technical Debt Metrics (SQALE)

| Metric | Description | Target |
|--------|-------------|--------|
| **Technical Debt Ratio** | Remediation cost / Development cost | < 5% |
| **Debt by Category** | Breakdown: reliability, security, maintainability | Dashboard |
| **New Debt** | Debt introduced in recent changes | Track |
| **Debt Hotspots** | Files with highest concentrated debt | Top 10 |
| **Remediation Time** | Estimated hours to fix all issues | Track |

### 12. Code Churn & Evolution Metrics (if git history available)

| Metric | Description | Target |
|--------|-------------|--------|
| **Churn Rate** | Lines changed / Total lines over time | Monitor |
| **Hotspot Files** | High churn + high complexity | Review |
| **Author Concentration** | Bus factor per module | > 2 |
| **Change Coupling** | Files that change together | Review |
| **Code Age** | Time since last modification | Monitor |
| **Refactoring Ratio** | Refactoring commits / Total commits | > 10% |

### 13. Documentation & Operational Readiness (DocOps Score)

This section evaluates the existence, quality, and completeness of documentation required for installing, managing, operating, and troubleshooting the codebase. Scoring follows the **Divio Documentation System** framework and **Google SRE Production Readiness** standards.

#### Installation & Setup Documentation
| Metric | Description | Target | Weight |
|--------|-------------|--------|--------|
| **README Exists** | Root README.md present | Yes | Required |
| **Quick Start Guide** | <5 minute setup instructions | Present | 10 pts |
| **Prerequisites Listed** | Runtime, dependencies, tools clearly stated | Complete | 10 pts |
| **Installation Steps** | Step-by-step installation instructions | Present | 15 pts |
| **Environment Setup** | .env.example, config templates provided | Present | 10 pts |
| **Reproducible Install** | Single command install (make, docker-compose, script) | Present | 15 pts |
| **Platform Coverage** | Instructions for all supported OS/platforms | Complete | 5 pts |
| **Dependency Pinning** | Lock files present (package-lock, Pipfile.lock, go.sum) | Present | 10 pts |

#### Repeatability & Reproducibility (Twelve-Factor App Compliance)
| Metric | Description | Target | Weight |
|--------|-------------|--------|--------|
| **Containerization** | Dockerfile/docker-compose.yml present | Present | 15 pts |
| **IaC Definitions** | Infrastructure as Code (Terraform, CloudFormation, etc.) | Present | 10 pts |
| **CI/CD Pipeline** | .github/workflows, .gitlab-ci.yml, Jenkinsfile, etc. | Present | 15 pts |
| **Build Determinism** | Reproducible builds documented/configured | Yes | 10 pts |
| **Config Externalization** | No hardcoded configs, env-based configuration | 100% | 10 pts |
| **Seed/Migration Scripts** | Database setup automation | Present | 10 pts |
| **Version Pinning** | All dependencies version-locked | 100% | 10 pts |

#### Operational Documentation (SRE/ITIL Standards)
| Metric | Description | Target | Weight |
|--------|-------------|--------|--------|
| **Architecture Docs** | System architecture diagrams (C4, UML, etc.) | Present | 15 pts |
| **ADRs Present** | Architecture Decision Records | > 3 | 10 pts |
| **Runbooks/Playbooks** | Operational procedures documented | Present | 15 pts |
| **Monitoring Guide** | How to monitor, what metrics matter | Present | 10 pts |
| **Alerting Documentation** | Alert definitions and response procedures | Present | 10 pts |
| **Scaling Guide** | How to scale horizontally/vertically | Present | 10 pts |
| **Backup/Recovery Docs** | Backup procedures and disaster recovery | Present | 15 pts |
| **SLA/SLO Definitions** | Service level objectives documented | Present | 10 pts |

#### Troubleshooting & Support Documentation
| Metric | Description | Target | Weight |
|--------|-------------|--------|--------|
| **FAQ/Known Issues** | Common problems and solutions | Present | 10 pts |
| **Debugging Guide** | How to debug common issues | Present | 15 pts |
| **Log Documentation** | Log formats, locations, and interpretation | Present | 10 pts |
| **Error Code Reference** | Error codes with explanations | Present | 10 pts |
| **Support Escalation** | How to get help, contact maintainers | Present | 5 pts |
| **Changelog Maintained** | CHANGELOG.md with recent updates | Present | 10 pts |
| **Breaking Changes Noted** | Migration guides for major versions | Present | 10 pts |

#### API & Developer Documentation (Divio Framework)
| Metric | Description | Target | Weight |
|--------|-------------|--------|--------|
| **Tutorials** | Learning-oriented, step-by-step guides | Present | 15 pts |
| **How-To Guides** | Task-oriented, problem-solving guides | Present | 15 pts |
| **Reference Docs** | Information-oriented, API specifications | Present | 20 pts |
| **Explanation/Concepts** | Understanding-oriented, background info | Present | 10 pts |
| **Code Examples** | Working examples for public APIs | > 50% | 15 pts |
| **API Versioning Docs** | Version compatibility documented | Present | 10 pts |
| **OpenAPI/Swagger Spec** | Machine-readable API specification | Present | 15 pts |

#### Documentation Quality Metrics
| Metric | Description | Target |
|--------|-------------|--------|
| **Doc Freshness** | Last updated within 90 days of code changes | > 80% |
| **Broken Links** | Invalid internal/external links | 0 |
| **Spelling/Grammar** | Documentation quality score | > 90% |
| **Reading Level** | Flesch-Kincaid grade level | 8-12 |
| **Completeness Score** | Sections present vs. expected | > 80% |
| **Searchability** | Documentation indexed/searchable | Yes |

#### DocOps Scoring Summary
| Grade | Score Range | Description |
|-------|-------------|-------------|
| **A** | 90-100 | Production-ready, comprehensive documentation |
| **B** | 75-89 | Good documentation, minor gaps |
| **C** | 60-74 | Adequate documentation, notable gaps |
| **D** | 40-59 | Minimal documentation, significant gaps |
| **F** | 0-39 | Insufficient documentation, high operational risk |

#### Industry Standards & Benchmarks

| Standard | Description | Key Requirements |
|----------|-------------|------------------|
| **ISO/IEC 25010 (SQuaRE)** | Software quality model | Documentation as part of usability and maintainability |
| **Twelve-Factor App** | SaaS best practices | Config, dependencies, build/release/run separation |
| **Google SRE PRR** | Production Readiness Review | Monitoring, alerting, capacity planning docs |
| **ITIL v4** | IT Service Management | Operational documentation, runbooks, known error database |
| **DORA Metrics** | DevOps performance | Deployment documentation, change failure rate tracking |
| **IEEE 1063** | Software User Documentation | Structure, content, format standards |
| **ISO/IEC/IEEE 26511** | Systems and software engineering — Requirements for managers of information for users | Documentation lifecycle management |

### 14. AWS Well-Architected Framework Alignment

This section evaluates code-level patterns and practices that align with the six pillars of the AWS Well-Architected Framework. While the framework is cloud-focused, these patterns apply to any production-grade software.

#### Operational Excellence (Code-Level)
| Metric | Description | Detection | Target |
|--------|-------------|-----------|--------|
| **Structured Logging** | Consistent log format with context (JSON, correlation IDs) | Log statements with structured format | 100% |
| **Log Levels Proper Use** | Appropriate DEBUG/INFO/WARN/ERROR usage | Log level distribution analysis | Balanced |
| **Metrics Instrumentation** | Code emits custom metrics (counters, gauges, histograms) | Metrics library usage | Present |
| **Distributed Tracing** | Trace context propagation (OpenTelemetry, X-Ray, Jaeger) | Tracing library/decorator usage | Present |
| **Health Check Endpoints** | /health, /ready, /live endpoints implemented | Endpoint detection | Present |
| **Feature Flags** | Runtime feature toggle capability | Feature flag library/pattern usage | Present |
| **Graceful Shutdown** | Signal handling, connection draining | SIGTERM handlers, shutdown hooks | Present |
| **Configuration Externalization** | No hardcoded configs, env/config file based | Hardcoded value detection | 100% |

#### Security (Code-Level)
| Metric | Description | Detection | Target |
|--------|-------------|-----------|--------|
| **Input Validation** | All external inputs validated/sanitized | Validation patterns at boundaries | 100% |
| **Output Encoding** | Proper encoding for context (HTML, SQL, shell) | Encoding function usage | 100% |
| **Authentication Checks** | Auth verification on protected endpoints | Auth middleware/decorator presence | 100% |
| **Authorization Checks** | Permission verification before operations | Authz patterns on sensitive operations | 100% |
| **Secrets Management** | No hardcoded secrets, uses secret managers | Secret pattern detection, env usage | 0 hardcoded |
| **Secure Defaults** | Security-conscious default configurations | Default value analysis | Yes |
| **Audit Logging** | Security-relevant events logged | Audit log patterns on sensitive ops | Present |
| **Cryptography Usage** | Proper crypto primitives, no custom crypto | Crypto library analysis | Standards only |

#### Reliability (Code-Level)
| Metric | Description | Detection | Target |
|--------|-------------|-----------|--------|
| **Circuit Breaker Pattern** | Prevents cascade failures to downstream services | Circuit breaker library/pattern usage | Present |
| **Retry with Backoff** | Transient failure handling with exponential backoff | Retry pattern detection | Present |
| **Timeout Configuration** | All external calls have timeouts | HTTP/DB client timeout settings | 100% |
| **Bulkhead Pattern** | Resource isolation (thread pools, connection limits) | Pool/limiter configurations | Present |
| **Fallback Mechanisms** | Graceful degradation when dependencies fail | Fallback/default value patterns | Present |
| **Idempotency** | Safe retry of operations (idempotency keys) | Idempotent operation patterns | Where needed |
| **Dead Letter Handling** | Failed message/event handling strategy | DLQ configuration, error handlers | Present |
| **Connection Pooling** | Reuse of expensive connections (DB, HTTP) | Pool configuration detection | Present |
| **Error Classification** | Retryable vs non-retryable error handling | Error type differentiation | Present |

#### Performance Efficiency (Code-Level)
| Metric | Description | Detection | Target |
|--------|-------------|-----------|--------|
| **Caching Strategy** | Appropriate use of caching layers | Cache library usage, TTL configs | Present |
| **Async/Non-Blocking I/O** | Non-blocking operations for I/O bound work | Async pattern usage | Where appropriate |
| **Batch Operations** | Bulk processing instead of N+1 queries | Batch API usage, query analysis | Present |
| **Lazy Loading** | Deferred initialization of expensive resources | Lazy initialization patterns | Where appropriate |
| **Connection Reuse** | HTTP keep-alive, connection pooling | Client configuration analysis | Present |
| **Pagination** | Large result sets paginated | Pagination parameter handling | Present |
| **Streaming** | Large data handled as streams vs loading in memory | Stream API usage for large data | Where appropriate |
| **Index Awareness** | Database queries leverage indexes | Query pattern analysis | Present |
| **N+1 Query Detection** | Identification of N+1 query patterns | ORM usage patterns, query loops | 0 |

#### Cost Optimization (Code-Level)
| Metric | Description | Detection | Target |
|--------|-------------|-----------|--------|
| **Resource Cleanup** | Proper disposal of connections, handles, memory | try-finally, using, defer patterns | 100% |
| **Efficient Algorithms** | Appropriate algorithm complexity for data size | Algorithm complexity analysis | O(n log n) or better |
| **Right-Sized Data Structures** | Appropriate collection types and initial sizes | Collection usage patterns | Appropriate |
| **Compute Optimization** | Avoiding unnecessary computation | Memoization, early returns | Present |
| **Transfer Optimization** | Compression, minimal payloads | Compression settings, DTO patterns | Present |
| **Storage Efficiency** | Appropriate data types, normalization | Schema analysis | Appropriate |
| **Cold Start Optimization** | Minimal initialization for serverless | Init code analysis | < 1s |
| **Scheduled Resource Management** | Non-critical resources scaled down off-hours | Schedule-aware patterns | Where applicable |

#### Sustainability (Code-Level)
| Metric | Description | Detection | Target |
|--------|-------------|-----------|--------|
| **Efficient Resource Utilization** | Maximizing work per compute cycle | Resource efficiency patterns | High |
| **Workload Optimization** | Batch processing during low-carbon periods | Scheduling patterns | Where applicable |
| **Data Lifecycle Management** | TTL on data, archival strategies | Retention policies, cleanup jobs | Present |
| **Right-Sizing Queries** | Fetching only needed data (SELECT specific columns) | Query selectivity analysis | 100% |
| **Minimize Data Movement** | Processing data close to source | Data locality patterns | Where applicable |
| **Efficient Serialization** | Binary formats where appropriate (protobuf, msgpack) | Serialization library usage | Where appropriate |
| **Green Scheduling** | Deferrable work scheduled for low-impact times | Scheduling flexibility | Where applicable |

#### Well-Architected Scoring Summary
| Pillar | Score | Grade |
|--------|-------|-------|
| **Operational Excellence** | 0-100 | A-F |
| **Security** | 0-100 | A-F |
| **Reliability** | 0-100 | A-F |
| **Performance Efficiency** | 0-100 | A-F |
| **Cost Optimization** | 0-100 | A-F |
| **Sustainability** | 0-100 | A-F |
| **Overall Well-Architected Score** | 0-100 | A-F |

#### Well-Architected Anti-Patterns
| Anti-Pattern | Pillar | Detection | Severity |
|--------------|--------|-----------|----------|
| **Missing Timeouts** | Reliability | External calls without timeout config | High |
| **No Retry Logic** | Reliability | HTTP/RPC calls without retry handling | Medium |
| **Synchronous Chains** | Performance | Long synchronous call chains for I/O | Medium |
| **Unbounded Queries** | Performance, Cost | SELECT * without LIMIT, missing pagination | High |
| **Missing Circuit Breakers** | Reliability | Direct calls to external services | Medium |
| **Hardcoded Endpoints** | Operational Excellence | Service URLs in code vs config | Medium |
| **Missing Health Checks** | Operational Excellence | No health/ready endpoints | High |
| **Unstructured Logging** | Operational Excellence | print/console.log without structure | Medium |
| **Missing Input Validation** | Security | Direct use of user input | Critical |
| **Secrets in Code** | Security | Passwords, keys in source files | Critical |
| **No Resource Cleanup** | Cost, Reliability | Missing close/dispose/cleanup | High |
| **N+1 Queries** | Performance, Cost | Query inside loop patterns | High |
| **Missing Idempotency** | Reliability | Non-idempotent retry-able operations | Medium |
| **Blocking Main Thread** | Performance | Sync I/O on event loop/main thread | High |

## Output Format

Generate `data.json` with this structure:
```json
{
  "project": "project-name",
  "analyzed_at": "ISO-8601 timestamp",
  "languages_detected": ["java", "terraform"],
  "summary": {
    "total_sloc": number,
    "avg_complexity": number,
    "avg_cognitive_complexity": number,
    "avg_maintainability": number,
    "anti_patterns_per_1k": number,
    "api_surface_total": number,
    "security_score": number,
    "test_coverage": number,
    "technical_debt_hours": number,
    "solid_score": number,
    "health_grade": "A-F"
  },
  "call_stack_analysis": {
    "max_depth": number,
    "avg_depth": number,
    "deepest_chains": [
      {
        "entry_point": "string",
        "depth": number,
        "path": ["file1:method1", "file2:method2"]
      }
    ]
  },
  "change_impact": {
    "avg_files_per_change": number,
    "avg_apis_per_change": number,
    "high_blast_radius_files": [],
    "hub_files": [],
    "circular_dependencies": []
  },
  "coupling_metrics": {
    "by_module": [
      {
        "module": "string",
        "afferent_coupling": number,
        "efferent_coupling": number,
        "instability": number,
        "abstractness": number,
        "distance_main_sequence": number
      }
    ]
  },
  "ck_metrics": {
    "by_class": [
      {
        "class": "string",
        "wmc": number,
        "dit": number,
        "noc": number,
        "cbo": number,
        "rfc": number,
        "lcom": number
      }
    ]
  },
  "design_patterns": {
    "detected": [
      {
        "pattern": "Repository",
        "confidence": 0.95,
        "locations": ["UserRepository.java", "OrderRepository.java"]
      }
    ],
    "anti_patterns": [
      {
        "pattern": "God Class",
        "severity": "high",
        "locations": ["MonolithService.java"]
      }
    ]
  },
  "solid_compliance": {
    "single_responsibility": number,
    "open_closed": number,
    "liskov_substitution": number,
    "interface_segregation": number,
    "dependency_inversion": number,
    "violations": []
  },
  "by_language": {
    "java": {
      "sloc": number,
      "complexity": number,
      "maintainability": number,
      "file_count": number
    }
  },
  "by_directory": [
    {
      "path": "src/main/java",
      "sloc": number,
      "complexity": number,
      "maintainability": number,
      "anti_patterns": number
    }
  ],
  "by_file": [
    {
      "path": "src/main/java/Example.java",
      "sloc": number,
      "complexity": number,
      "cognitive_complexity": number,
      "maintainability": number,
      "anti_patterns": [],
      "fan_in": number,
      "fan_out": number,
      "change_risk": "low|medium|high"
    }
  ],
  "anti_patterns": {
    "god_classes": {
      "count": number,
      "per_1k": number,
      "severity": "high",
      "locations": [
        {
          "file": "path/to/file",
          "line": number,
          "snippet": "code excerpt",
          "remediation": "suggestion"
        }
      ]
    }
  },
  "api_surface": {
    "rest_endpoints": {
      "count": number,
      "items": [
        {
          "method": "GET",
          "path": "/api/users",
          "location": "UserController.java:45"
        }
      ]
    }
  },
  "security": {
    "public_exposure_score": number,
    "encryption_coverage": number,
    "iam_least_privilege_score": number,
    "vulnerability_count": {
      "critical": number,
      "high": number,
      "medium": number,
      "low": number
    },
    "findings": []
  },
  "testing": {
    "coverage_line": number,
    "coverage_branch": number,
    "test_to_code_ratio": number,
    "test_count": number,
    "assertion_density": number
  },
  "documentation": {
    "public_api_documented": number,
    "readme_score": number,
    "missing_docs": []
  },
  "docops": {
    "overall_score": number,
    "overall_grade": "A-F",
    "installation": {
      "score": number,
      "readme_exists": boolean,
      "quick_start": boolean,
      "prerequisites_listed": boolean,
      "installation_steps": boolean,
      "env_setup": boolean,
      "reproducible_install": boolean,
      "platform_coverage": number,
      "dependency_pinning": boolean
    },
    "repeatability": {
      "score": number,
      "containerization": boolean,
      "iac_definitions": boolean,
      "ci_cd_pipeline": boolean,
      "build_determinism": boolean,
      "config_externalization": number,
      "seed_migration_scripts": boolean,
      "version_pinning": number
    },
    "operational": {
      "score": number,
      "architecture_docs": boolean,
      "adrs_count": number,
      "runbooks": boolean,
      "monitoring_guide": boolean,
      "alerting_docs": boolean,
      "scaling_guide": boolean,
      "backup_recovery_docs": boolean,
      "sla_slo_definitions": boolean
    },
    "troubleshooting": {
      "score": number,
      "faq_exists": boolean,
      "debugging_guide": boolean,
      "log_documentation": boolean,
      "error_code_reference": boolean,
      "support_escalation": boolean,
      "changelog_maintained": boolean,
      "breaking_changes_noted": boolean
    },
    "developer_docs": {
      "score": number,
      "tutorials": boolean,
      "how_to_guides": boolean,
      "reference_docs": boolean,
      "explanation_concepts": boolean,
      "code_examples_coverage": number,
      "api_versioning_docs": boolean,
      "openapi_spec": boolean
    },
    "quality": {
      "doc_freshness": number,
      "broken_links": number,
      "spelling_grammar_score": number,
      "reading_level": number,
      "completeness_score": number,
      "searchability": boolean
    },
    "missing_documentation": [],
    "recommendations": []
  },
  "well_architected": {
    "overall_score": number,
    "overall_grade": "A-F",
    "operational_excellence": {
      "score": number,
      "structured_logging": boolean,
      "log_levels_proper": boolean,
      "metrics_instrumentation": boolean,
      "distributed_tracing": boolean,
      "health_checks": boolean,
      "feature_flags": boolean,
      "graceful_shutdown": boolean,
      "config_externalization": number
    },
    "security": {
      "score": number,
      "input_validation": number,
      "output_encoding": number,
      "auth_checks": number,
      "authz_checks": number,
      "secrets_management": boolean,
      "secure_defaults": boolean,
      "audit_logging": boolean,
      "crypto_usage": "standards|custom|none"
    },
    "reliability": {
      "score": number,
      "circuit_breakers": boolean,
      "retry_with_backoff": boolean,
      "timeout_configuration": number,
      "bulkhead_pattern": boolean,
      "fallback_mechanisms": boolean,
      "idempotency": boolean,
      "dead_letter_handling": boolean,
      "connection_pooling": boolean,
      "error_classification": boolean
    },
    "performance_efficiency": {
      "score": number,
      "caching_strategy": boolean,
      "async_io": boolean,
      "batch_operations": boolean,
      "lazy_loading": boolean,
      "connection_reuse": boolean,
      "pagination": boolean,
      "streaming": boolean,
      "index_awareness": boolean,
      "n_plus_1_queries": number
    },
    "cost_optimization": {
      "score": number,
      "resource_cleanup": number,
      "efficient_algorithms": boolean,
      "right_sized_structures": boolean,
      "compute_optimization": boolean,
      "transfer_optimization": boolean,
      "storage_efficiency": boolean,
      "cold_start_optimization": boolean
    },
    "sustainability": {
      "score": number,
      "efficient_utilization": boolean,
      "data_lifecycle_management": boolean,
      "right_sizing_queries": number,
      "efficient_serialization": boolean
    },
    "anti_patterns": [
      {
        "pattern": "string",
        "pillar": "string",
        "severity": "critical|high|medium|low",
        "locations": []
      }
    ]
  },
  "technical_debt": {
    "total_hours": number,
    "ratio": number,
    "by_category": {
      "reliability": number,
      "security": number,
      "maintainability": number
    },
    "hotspots": []
  },
  "recommendations": {
    "immediate": [],
    "short_term": [],
    "long_term": []
  }
}
```

Generate `index.html` as a self-contained dashboard with:

**Summary Section**
- Overall health grade (A-F) with color coding
- Key metrics cards with trend indicators
- Radar chart for SOLID compliance
- Language breakdown pie chart

**Call Stack & Coupling Section**
- Call depth distribution histogram
- Dependency graph visualization (D3.js force-directed)
- Circular dependency warnings
- Hub files table
- Change impact heat map

**Code Quality Section**
- Complexity distribution histogram
- Maintainability heat map by directory
- Cognitive complexity trends
- Duplication report

**Design Patterns Section**
- Detected patterns list with confidence scores
- Anti-pattern findings with severity
- SOLID principle scores with drill-down
- Pattern usage recommendations

**Anti-Patterns Section**
- Sortable/filterable table of all findings
- Severity breakdown pie chart
- Remediation effort estimates
- Quick-fix suggestions

**API Surface Section**
- API explorer tree view
- Endpoint documentation
- Breaking change risk indicators

**Security Section**
- Vulnerability summary
- Security score gauge
- IaC misconfigurations
- Compliance checklist

**Testing Section**
- Coverage metrics
- Test quality indicators
- Untested code hotspots

**Technical Debt Section**
- Debt timeline (if history available)
- Debt by category
- Remediation roadmap

**DocOps & Operational Readiness Section**
- Overall DocOps grade with breakdown
- Installation readiness checklist (visual checkmarks)
- Repeatability score gauge
- Documentation coverage radar chart (Installation, Operational, Troubleshooting, Developer)
- Missing documentation checklist with priority ranking
- Industry standard compliance badges (Twelve-Factor, SRE PRR, ITIL)
- Time-to-first-deploy estimate based on documentation completeness

**Well-Architected Framework Section**
- Six-pillar radar chart (Operational Excellence, Security, Reliability, Performance, Cost, Sustainability)
- Overall Well-Architected score gauge
- Per-pillar breakdown with drill-down to specific metrics
- Anti-pattern findings table with severity indicators
- Resiliency patterns coverage (circuit breakers, retries, timeouts)
- Observability maturity score (logging, metrics, tracing)
- Production readiness checklist based on Well-Architected principles
- Comparison to AWS Well-Architected benchmarks

**Implementation Requirements**
- Use Chart.js for charts
- Use D3.js for dependency graphs
- Responsive design
- Dark/light mode toggle
- Collapsible sections
- Print-optimized CSS (@media print)
- **CRITICAL: Single-Page Layout** - Do NOT use tabs or hidden sections. All content MUST be visible on a single scrollable page. This ensures:
  - Users can print to PDF directly from browser
  - Users can take full-page screenshots
  - Content is accessible without JavaScript interaction
  - PDF exports capture all content

**PDF/PNG Export Requirements**
- Include html2pdf.js (CDN: https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js)
- Add TWO export buttons: "📄 Export PDF" and "🖼️ Export PNG"
- Use these EXACT html2pdf.js settings for high-quality output:
```javascript
const opt = {
    margin: [10, 10, 10, 10],
    filename: filename,
    image: { type: 'png', quality: 1.0 },  // PNG format, max quality
    html2canvas: {
        scale: 4,           // 4x scale for crisp high-DPI rendering
        useCORS: true,
        logging: false,
        allowTaint: true,
        backgroundColor: null  // Preserve transparency
    },
    jsPDF: {
        unit: 'mm',
        format: 'a4',
        orientation: 'portrait',
        compress: true
    },
    pagebreak: { mode: ['avoid-all', 'css', 'legacy'] }
};
```
- **Chart.js Wait Logic**: Before capturing, wait for ALL charts to be ready using this pattern:
```javascript
function waitForCharts() {
    return new Promise((resolve) => {
        const checkCharts = () => {
            const canvases = document.querySelectorAll('canvas');
            const allReady = Array.from(canvases).every(canvas => {
                const chart = Chart.getChart(canvas);
                return chart && chart.ctx;
            });
            if (allReady) {
                // Additional delay for animation completion
                setTimeout(resolve, 500);
            } else {
                requestAnimationFrame(checkCharts);
            }
        };
        checkCharts();
    });
}
```
- **PNG Export Function**: Add standalone PNG export that captures the full page:
```javascript
async function exportPNG() {
    await waitForCharts();
    const element = document.querySelector('.container');
    const canvas = await html2canvas(element, {
        scale: 4,
        useCORS: true,
        logging: false,
        allowTaint: true
    });
    const link = document.createElement('a');
    link.download = filename.replace('.pdf', '.png');
    link.href = canvas.toDataURL('image/png');
    link.click();
}
```
- Auto-export should use `waitForCharts()` instead of fixed `setTimeout()`

**Footer Requirements**
- Footer text MUST be exactly: `Generated by [d-e-v.com](https://d-e-v.com) Ai Claude Code Review | [GitHub Project](https://github.com/d-e-v-com/Ai-prompts/blob/master/CLAUDE_CODE_REVIEW.md) | Report Date: YYYY-MM-DD`
- ALWAYS include d-e-v.com link: https://d-e-v.com
- GitHub Project link MUST point to: https://github.com/d-e-v-com/Ai-prompts/blob/master/CLAUDE_CODE_REVIEW.md
- Do NOT link to anthropic.com or claude.ai

**Search & Filter**
- Search/filter functionality for anti-patterns table

---

Generate `YYYY-MM-DD_CODEBASE-NAME_ACTION_ITEMS.md` as an actionable remediation plan:

**File Naming:** Use the same date and codebase name pattern (e.g., `2026-01-20_MyProject_ACTION_ITEMS.md`)

**Document Structure:**

```markdown
# Action Items: [Project Name] Code Review
**Generated:** YYYY-MM-DD
**Health Grade:** [A-F]
**Total Issues:** X (Critical: X, High: X, Medium: X, Low: X)
**Estimated Total Effort:** X hours

---

## Executive Summary

[2-3 paragraph overview of the codebase health, major concerns, and recommended priorities]

### Critical Metrics
| Metric | Value | Target | Status |
|--------|-------|--------|--------|
| Maintainability Index | XX | >65 | ⚠️/✅/❌ |
| Cyclomatic Complexity | XX | <10 | ⚠️/✅/❌ |
| Security Score | XX | >80 | ⚠️/✅/❌ |
| Test Coverage | XX% | >80% | ⚠️/✅/❌ |
| Technical Debt | XX hrs | <40 hrs | ⚠️/✅/❌ |

---

## Findings Summary

### By Severity
- **Critical (P0):** X issues - Immediate attention required
- **High (P1):** X issues - Address within current sprint
- **Medium (P2):** X issues - Plan for next sprint
- **Low (P3):** X issues - Backlog

### By Category
- Security Vulnerabilities: X
- Anti-Patterns: X
- Code Smells: X
- Performance Issues: X
- Documentation Gaps: X

---

## Remediation Plan

### Epic 1: [Category - e.g., "Security Hardening"]
**Priority:** Critical
**Total Effort:** X hours
**Description:** [Why this epic matters and what it addresses]

---

#### Story 1.1: [Specific Issue - e.g., "Fix SQL Injection Vulnerabilities"]
**Priority:** Critical (P0)
**Effort:** X hours
**Labels:** `security`, `sql-injection`, `owasp-top-10`

**Description:**
[Detailed explanation of the issue, why it's a problem, and the business impact]

**Affected Files:**
| File | Line(s) | Issue |
|------|---------|-------|
| `/full/path/to/UserRepository.js` | 45-52 | Raw SQL query with string concatenation |
| `/full/path/to/OrderService.js` | 123 | Unparameterized query in search function |

**Acceptance Criteria:**
- [ ] All database queries use parameterized statements
- [ ] No string concatenation in SQL queries
- [ ] Input validation added for all user-supplied parameters
- [ ] Unit tests cover SQL injection edge cases
- [ ] Security scan passes with no SQL injection findings

**Subtasks:**

##### Subtask 1.1.1: Refactor UserRepository.js query methods
**File:** `/full/path/to/UserRepository.js`
**Lines:** 45-52
**Effort:** 1 hour

**Current Code:**
\`\`\`javascript
const query = "SELECT * FROM users WHERE id = " + userId;
\`\`\`

**Required Change:**
\`\`\`javascript
const query = "SELECT * FROM users WHERE id = ?";
db.execute(query, [userId]);
\`\`\`

**Steps:**
1. Replace string concatenation with parameterized query
2. Update all callers to pass parameters correctly
3. Add input validation for userId
4. Write unit test for edge cases (null, special characters)

---

##### Subtask 1.1.2: Refactor OrderService.js search function
**File:** `/full/path/to/OrderService.js`
**Lines:** 123
**Effort:** 1.5 hours

[Same detailed format...]

---

#### Story 1.2: [Next Story...]
[Same format...]

---

### Epic 2: [Next Category - e.g., "Code Quality Improvements"]
[Same format...]

---

## Appendix

### High-Risk Files (Top 10)
| File | Complexity | Maintainability | Issues | Risk |
|------|------------|-----------------|--------|------|
| `/path/to/file1.js` | 45 | 32 | 8 | Critical |
| `/path/to/file2.js` | 38 | 41 | 5 | High |

### Anti-Pattern Locations
[Full list of detected anti-patterns with file:line references]

### Circular Dependencies
[List of circular dependency chains that need breaking]
```

**Content Requirements:**

1. **Prioritization**
   - Order Epics by severity: Critical → High → Medium → Low
   - Within each Epic, order Stories by effort-to-impact ratio
   - Group related issues into logical Epics

2. **File References**
   - ALWAYS include full absolute paths (e.g., `/src/services/UserService.js`)
   - ALWAYS include line numbers (e.g., `lines 45-67`)
   - Include the actual code snippet when helpful

3. **Actionable Details**
   - Each Subtask must be immediately actionable by AI or developer
   - Include "Current Code" and "Required Change" snippets where applicable
   - Provide step-by-step remediation instructions
   - Reference specific functions, classes, and variable names

4. **Acceptance Criteria**
   - Each Story must have testable acceptance criteria
   - Use checkbox format `- [ ]` for tracking
   - Be specific (not "improve code" but "reduce complexity below 10")

5. **Effort Estimates**
   - Base estimates on technical debt hours from analysis
   - Break down by Story and Subtask
   - Include total per Epic

6. **Cross-References**
   - Link related issues that should be fixed together
   - Note dependencies between Stories
   - Highlight files that appear in multiple issues (hotspots)

7. **Labels/Tags**
   - Include relevant labels for easy filtering (security, performance, refactoring, etc.)
   - Match common issue tracker taxonomies (OWASP, CWE for security)

---

Generate `YYYY-MM-DD_CODEBASE-NAME_ACTION_ITEMS.html` as a styled, printable HTML version:

**Purpose:** Intermediate file for PDF generation and browser viewing

**Requirements:**
- Self-contained HTML with embedded CSS (no external dependencies)
- Professional styling matching the dashboard theme (dark mode default)
- Print-optimized CSS (@media print) for clean PDF output
- Proper page breaks between Epics
- Syntax highlighting for code snippets
- Collapsible sections for Stories/Subtasks (expanded by default for PDF)
- Table of contents with anchor links
- Company-ready formatting suitable for executive sharing

**Styling:**
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Action Items: [Project Name]</title>
    <style>
        :root {
            --bg-primary: #1a1a2e;
            --bg-secondary: #16213e;
            --text-primary: #eee;
            --text-secondary: #a0a0a0;
            --accent-red: #e94560;
            --accent-green: #4ecca3;
            --accent-blue: #00d9ff;
            --accent-yellow: #ffc107;
        }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.6;
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px;
        }
        h1, h2, h3, h4 { color: var(--accent-blue); }
        .priority-critical { color: var(--accent-red); font-weight: bold; }
        .priority-high { color: #fd7e14; }
        .priority-medium { color: var(--accent-yellow); }
        .priority-low { color: var(--accent-green); }
        table { width: 100%; border-collapse: collapse; margin: 1em 0; }
        th, td { padding: 12px; text-align: left; border-bottom: 1px solid #333; }
        th { background: var(--bg-secondary); }
        code { background: #0d0d1a; padding: 2px 6px; border-radius: 4px; }
        pre { background: #0d0d1a; padding: 16px; border-radius: 8px; overflow-x: auto; }
        .checkbox { margin-right: 8px; }
        .label {
            display: inline-block;
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 0.8em;
            margin-right: 4px;
            background: var(--bg-secondary);
        }
        @media print {
            body { background: white; color: black; }
            h1, h2, h3, h4 { color: #1a1a2e; }
            .page-break { page-break-before: always; }
            pre, code { background: #f5f5f5; }
        }
    </style>
</head>
<body>
    <!-- Rendered markdown content here -->
</body>
</html>
```

---

Generate `YYYY-MM-DD_CODEBASE-NAME_ACTION_ITEMS.pdf` from the HTML:

**Purpose:** Executive-friendly PDF for email sharing

**Generation Method:**
Use the browser's built-in print-to-PDF functionality or include a script that auto-generates the PDF:

```javascript
// Include html2pdf.js in the ACTION_ITEMS.html
// <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

function exportActionItemsPDF() {
    const element = document.body;
    const filename = document.title.replace('Action Items: ', '') + '_ACTION_ITEMS.pdf';

    const opt = {
        margin: [15, 15, 15, 15],
        filename: filename,
        image: { type: 'png', quality: 1.0 },
        html2canvas: {
            scale: 3,
            useCORS: true,
            logging: false
        },
        jsPDF: {
            unit: 'mm',
            format: 'a4',
            orientation: 'portrait'
        },
        pagebreak: { mode: ['avoid-all', 'css', 'legacy'] }
    };

    html2pdf().set(opt).from(element).save();
}

// Auto-generate PDF on first load
if (!localStorage.getItem('action_items_pdf_exported_' + document.title)) {
    setTimeout(() => {
        exportActionItemsPDF();
        localStorage.setItem('action_items_pdf_exported_' + document.title, 'true');
    }, 1000);
}
```

**PDF Requirements:**
- A4 format, portrait orientation
- Clean margins (15mm)
- Page breaks between major sections (Epics)
- All code snippets readable
- Tables not cut off at page boundaries
- Professional appearance suitable for executive/stakeholder sharing

## Execution Steps

1. **Discovery Phase**
   - Detect primary language(s) by scanning file extensions
   - Identify project structure (monorepo, microservices, etc.)
   - Locate test directories
   - Find configuration files

2. **Exclusion Setup**
   - Exclude: vendor/, node_modules/, .git/, build/, dist/, target/, bin/, obj/
   - Exclude: .terraform/, .terragrunt-cache/
   - Exclude: Generated files (*.generated.*, *.g.cs, *.designer.cs)
   - Exclude: Test fixtures, mocks, snapshots

3. **Static Analysis**
   - For each source file:
     - Calculate SLOC (exclude blanks, comments)
     - Calculate cyclomatic complexity
     - Calculate cognitive complexity (SonarQube algorithm)
     - Calculate maintainability index
     - Parse AST for coupling analysis
     - Detect design patterns and anti-patterns
     - Identify language-specific issues

4. **Coupling & Call Stack Analysis**
   - Build dependency graph
   - Calculate fan-in/fan-out for each module
   - Detect circular dependencies
   - Trace call stacks from entry points
   - Calculate blast radius for each file
   - Identify hub files

5. **OO Metrics Calculation**
   - Calculate CK metrics for each class
   - Calculate MOOD metrics for project
   - Evaluate SOLID compliance

6. **IaC Security Analysis** (if applicable)
   - Run security checks
   - Identify misconfigurations
   - Calculate compliance coverage
   - Check for secrets

7. **Test Analysis** (if tests exist)
   - Calculate coverage metrics
   - Evaluate test quality
   - Identify untested code

8. **Documentation Analysis**
   - Check public API documentation
   - Evaluate README completeness
   - Find broken links

9. **Technical Debt Calculation**
   - Apply SQALE methodology
   - Estimate remediation time
   - Categorize issues

10. **Report Generation**
    - Aggregate metrics at file, directory, language, and project levels
    - Generate data.json with all findings
    - Generate index.html dashboard (single-page, no tabs)
    - Generate ACTION_ITEMS.md remediation plan
    - Generate ACTION_ITEMS.html styled version
    - Create dependency visualization

11. **Automatic PDF/PNG Export (REQUIRED)**
    - **MUST generate all PDF and PNG files automatically using headless browser**
    - Use puppeteer, playwright, or chrome/chromium in headless mode via bash
    - Generate these files automatically (do NOT rely on user clicking export buttons):
      - `YYYY-MM-DD_CODEBASE-NAME_CODE_REVIEW_AUDIT_REPORT.pdf` from index.html
      - `YYYY-MM-DD_CODEBASE-NAME_CODE_REVIEW_AUDIT_REPORT.png` from index.html
      - `YYYY-MM-DD_CODEBASE-NAME_ACTION_ITEMS.pdf` from ACTION_ITEMS.html
    - Example using puppeteer (install if needed: `npm install puppeteer`):
    ```bash
    node -e "
    const puppeteer = require('puppeteer');
    (async () => {
      const browser = await puppeteer.launch();
      const page = await browser.newPage();
      await page.goto('file://$(pwd)/index.html', {waitUntil: 'networkidle0'});
      await page.waitForTimeout(2000); // Wait for charts to render
      await page.pdf({path: 'REPORT.pdf', format: 'A4', printBackground: true});
      await page.screenshot({path: 'REPORT.png', fullPage: true});
      await browser.close();
    })();
    "
    ```
    - Alternative: Use chrome/chromium directly:
    ```bash
    # PDF export
    chromium --headless --disable-gpu --print-to-pdf=REPORT.pdf index.html
    # PNG export
    chromium --headless --disable-gpu --screenshot=REPORT.png --window-size=1400,10000 index.html
    ```
    - **All 7 output files MUST exist when task completes**

12. **Executive Summary**
    - Overall health grade with justification
    - Top 10 files needing immediate attention
    - Critical security findings
    - Recommended refactoring priorities
    - Estimated effort for improvements
    - Comparison to industry benchmarks

## Benchmark Targets (Industry Standards)

| Metric | Poor | Fair | Good | Excellent |
|--------|------|------|------|-----------|
| Maintainability Index | < 40 | 40-65 | 65-85 | > 85 |
| Cyclomatic Complexity (avg) | > 15 | 10-15 | 5-10 | < 5 |
| Cognitive Complexity (avg) | > 20 | 15-20 | 8-15 | < 8 |
| Technical Debt Ratio | > 20% | 10-20% | 5-10% | < 5% |
| Test Coverage | < 40% | 40-60% | 60-80% | > 80% |
| Duplication | > 10% | 5-10% | 3-5% | < 3% |
| LCOM (avg) | > 0.8 | 0.5-0.8 | 0.3-0.5 | < 0.3 |
| Coupling (CBO avg) | > 20 | 14-20 | 8-14 | < 8 |
| Call Stack Depth (max) | > 15 | 10-15 | 5-10 | < 5 |
| Files Per Change | > 10 | 5-10 | 3-5 | < 3 |
| Circular Dependencies | > 5 | 2-5 | 1-2 | 0 |
| DocOps Score | < 40 | 40-60 | 60-80 | > 80 |
| Installation Docs | Missing | Partial | Good | Complete |
| Operational Docs | None | Basic | Comprehensive | SRE-ready |
| Repeatability | Manual | Scripted | Containerized | Full IaC |
| Well-Architected Score | < 40 | 40-60 | 60-80 | > 80 |
| Observability | None | Logs only | Logs+Metrics | Full (L+M+T) |
| Resiliency Patterns | None | Basic retries | Partial | Circuit breakers+Bulkheads |
| Security Posture | Critical gaps | Some gaps | Good | Defense in depth |

Start by exploring the project structure to detect languages, then proceed with the full analysis. Provide progress updates for long-running operations.
```

---

This comprehensive prompt now includes:

1. **Call Stack & Coupling Analysis** - Max/avg call depth, blast radius, files per change, APIs per change
2. **Full CK Metrics Suite** - WMC, DIT, NOC, CBO, RFC, LCOM
3. **MOOD Metrics** - MHF, AHF, MIF, AIF, PF, CF
4. **Complete Design Pattern Detection** - All GoF patterns plus architectural patterns
5. **Comprehensive Anti-Pattern Detection** - Including Feature Envy, Shotgun Surgery, Message Chains, etc.
6. **SOLID Compliance Scoring** - Per-principle scoring with violation details
7. **Additional Languages** - Go, Rust, Kubernetes/Helm
8. **Test Quality Metrics** - Coverage, mutation score, assertion density
9. **Documentation Metrics** - API docs, README completeness
10. **Technical Debt (SQALE)** - Industry-standard debt calculation
11. **Code Churn Metrics** - If git history is available
12. **Industry Benchmarks** - Clear targets for all metrics
13. **DocOps & Operational Readiness** - Installation ease, repeatability, operational/troubleshooting docs (ISO/IEC 25010, Twelve-Factor, SRE PRR, ITIL compliance)
14. **AWS Well-Architected Framework Alignment** - Six-pillar code-level analysis (Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability)

Would you like me to add any additional metrics or expand on any particular area?

---

## Credits

**Code Review Tool & Logic Created by:** [Jacob Baloul](https://www.linkedin.com/in/jacovbaloul/)

**Inspired by:** [Professor Dries Buytaert's work](https://dri.es/measuring-drupal-core-code-complexity) on measuring Drupal core code complexity.

### Key References

- **[drupal-core-metrics](https://github.com/dbuytaert/drupal-core-metrics)** - Professor Dries Buytaert's original metrics analysis tool for Drupal core
- **[Measuring Drupal Code Complexity](https://dri.es/measuring-drupal-core-code-complexity)** - Blog post explaining the methodology

### Standards & Methodologies

- **Chidamber & Kemerer (CK) Metrics** - Original OO metrics suite (1994)
- **MOOD Metrics** - Metrics for Object-Oriented Design by Abreu & Carapuça
- **SonarQube Cognitive Complexity** - Industry standard complexity measurement
- **SQALE Method** - Software Quality Assessment based on Lifecycle Expectations
- **Divio Documentation System** - Four-part documentation framework
- **Google SRE Production Readiness Review** - Operational excellence standards
- **Twelve-Factor App** - Methodology for building SaaS applications
- **ISO/IEC 25010 (SQuaRE)** - Systems and software quality models
- **ITIL v4** - IT Service Management best practices
- **DORA Metrics** - DevOps Research and Assessment performance metrics
- **[AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)** - Six pillars for building secure, high-performing, resilient, and efficient infrastructure

### License

MIT License - See [LICENSE](LICENSE) for details.

This work is inspired by [drupal-core-metrics](https://github.com/dbuytaert/drupal-core-metrics) by Professor Dries Buytaert.
