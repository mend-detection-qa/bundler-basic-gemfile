# bundler-basic-gemfile

## Feature exercised

Basic Gemfile + Gemfile.lock detection using a single rubygems.org source with direct runtime dependencies and their transitive dependencies, verifying that Mend SCA correctly identifies a Ruby/Bundler project at all (P0 foundation probe).

## Expected dependency tree

Direct dependencies (4):

- `rack` 3.0.10 — rubygems.org, no transitive deps
- `sinatra` 4.0.0 — rubygems.org, has transitive deps
- `multi_json` 1.15.0 — rubygems.org, leaf node (zero transitive deps)
- `faraday` 2.9.0 — rubygems.org, has transitive deps

Transitive dependencies (5):

- `mustermann` 3.0.0 — child of sinatra
- `rack-protection` 4.0.0 — child of sinatra
- `tilt` 2.4.0 — child of sinatra
- `faraday-net_http` 3.0.2 — child of faraday
- `ruby2_keywords` 0.0.5 — child of faraday and mustermann (deduplicated)

All dependencies are sourced from `https://rubygems.org/`. No git sources, no path sources, no gemspec. No group blocks — all gems are in the default runtime group.

## Probe metadata

| Field | Value |
|---|---|
| Pattern | bundler-basic-gemfile |
| Target | local |
| Package manager | Bundler / RUBYGEMS |
| Source | rubygems.org |
| Direct deps | 4 |
| Transitive deps | 5 |
| Total deps | 9 |
| Ruby version | >= 3.2 |
| Bundler version | 2.5.3 |
| Generated | 2026-04-27 |
