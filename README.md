# Budget-constrained MO-FCTP benchmark instances

This dataset contains ten instances of the multi-objective fixed-charge
transportation problem with destination budget constraints. Each instance is
available as a standalone JSON file with the same fields and layout. Each row
of a cost matrix occupies one line.

## File format

Let `m` be the number of sources, `n` the number of destinations, and `k`
the number of transport entries. All data values are integers.

| Field | Shape | Meaning |
| --- | --- | --- |
| `instance_id` | Scalar | Original instance number |
| `supply` | `m` | Supply by source |
| `demand` | `n` | Demand by destination |
| `transport` | `k` | Values from the original transport vector, in source-file order |
| `variable_costs` | `(k * m) × n` | Variable cost matrix |
| `fixed_costs` | `(k * m) × n` | Fixed cost matrix |
| `time_costs` | `(k * m) × n` | Time cost matrix |
| `destination_budgets` | `n` | Budget limit by destination |

Cost matrix columns follow the order of the `demand` and
`destination_budgets` vectors. The rows appear to be grouped by transport
type, with one row per source in each group. Under this interpretation, use
`matrix[t * m + i][j]` for transport type `t`, source `i`, and destination
`j`, using zero-based indices. 

The JSON files preserve the original row order. The supplied files label
the transport vector only as `transport`; its exact model role and the
units of the data are unspecified in those files.


