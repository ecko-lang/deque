# Deque - Ecko Std Lib Package

A double-ended queue for [Ecko](https://ecko.sh), written in Ecko - push, pop,
and peek at **both ends** with amortized O(1) cost.

## Install

```bash
ecko get github.com/ecko-lang/deque
```

## Usage

```ecko
import deque

q = deque.new()
q = deque.push_back(q, 1)
q = deque.push_front(q, 0)
r = deque.pop_front(q)          # [0, new_deque]
deque.peek_back(q)              # 1
deque.to_list(q)                # [0, 1]
```

## API

| Function | Description |
|---|---|
| `new()` · `from_list(l)` | build a deque |
| `push_front(q, x)` · `push_back(q, x)` | add an element, returning a new deque |
| `pop_front(q)` · `pop_back(q)` | `[value, new_deque]` (raises kind-`"value"` if empty) |
| `peek_front(q)` · `peek_back(q)` | the end element, or `null` |
| `size(q)` · `is_empty(q)` · `to_list(q)` | count / emptiness / a plain list |

Represented as two stacks `{ f, b }` (order = `reverse(f) ++ b`), so each op is a
cheap stack move with an occasional O(n) rebalance amortized away. Immutable -
every op returns a new deque.

## Testing

```bash
ecko test tests/
```

## License

MIT - see [LICENSE](LICENSE).
