# Celluloid 0.18.0 Upgrade Fixes

## Summary
Fixed compatibility issues with Celluloid 0.18.0 upgrade. The main changes were related to API changes in Celluloid's proxy and supervision systems.

## Changes Made

### 1. Updated Call ActorProxy class (lib/adhearsion/call.rb:20)
**Issue**: `Celluloid::CellProxy` no longer exists in Celluloid 0.18.0

**Fix**: Changed from `Celluloid::CellProxy` to `Celluloid::Proxy::Cell`

```ruby
# Before:
class ActorProxy < Celluloid::CellProxy

# After:
class ActorProxy < Celluloid::Proxy::Cell
```

### 2. Updated RSpec mock configuration (spec/spec_helper.rb:37)
**Issue**: `Celluloid::AbstractProxy` was renamed in Celluloid 0.18.0

**Fix**: Changed from `Celluloid::AbstractProxy` to `Celluloid::Proxy::Abstract`

```ruby
# Before:
mocks.add_stub_and_should_receive_to Celluloid::AbstractProxy

# After:
mocks.add_stub_and_should_receive_to Celluloid::Proxy::Abstract
```

### 3. Updated Statistics supervision (lib/adhearsion.rb:74)
**Issue**: `supervise_as` method signature changed in Celluloid 0.18.0

**Fix**: Changed from `supervise_as :name` to `supervise as: :name`

```ruby
# Before:
Statistics.supervise_as :statistics

# After:
Statistics.supervise as: :statistics
```

### 4. Updated HTTP Server supervision (lib/adhearsion/http_server.rb:30)
**Issue**: `supervise_as` method signature changed and requires args to be passed differently

**Fix**: Changed from `supervise_as(:name, arg1, arg2)` to `supervise as: :name, args: [arg1, arg2]`

```ruby
# Before:
supervisor = ::Reel::Rack::Server.supervise_as(:ahn_http_server, app, options)

# After:
supervisor = ::Reel::Rack::Server.supervise as: :ahn_http_server, args: [app, options]
```

## Test Results
All 259 examples in spec/adhearsion_spec.rb now pass with 0 failures.

## References
- Celluloid 0.18.0 moved proxy classes to `Celluloid::Proxy::*` namespace
- Supervision API changed from `supervise_as(:name)` to `supervise(as: :name)`
- Constructor arguments for supervised actors must be passed via `args:` parameter
