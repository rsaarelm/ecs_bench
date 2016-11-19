# Benchmarks of various Rust Entity Component Systems

## Benchmarks
Benchmarks are run on [Travis CI](https://travis-ci.org/lschmierer/ecs_bench/).

Benchmarks are located in `benches/[bench_name]_[ecs_crate_name].rs`.

 Benchmark       | [ecs](https://github.com/HeroesGrave/ecs-rs) | [specs](https://github.com/slide-rs/specs) | [recs](https://github.com/andybarron/rustic-ecs) | [trex](https://github.com/rcolinray/trex) | [calx-ecs](https://github.com/rsaarelm/calx-ecs)
 --------------- |:--------------------------------------------:|:------------------------------------------:|:------------------------------------------------:|:-----------------------------------------:|:-----------------------------------------:
 pos_vel build   | 1,153,406 ns/iter (+/- 15,423)                          | 261,635 ns/iter (+/- 4,441)                      | 7,670,432 ns/iter (+/- 272,428)                             | 673,889 ns/iter (+/- 9,300)                      | 1,075,719 ns/iter (+/- 15,129)
 pos_vel update  | 259,833 ns/iter (+/- 4,929)                         | 28,316 ns/iter (+/- 1,073)                     | 2,913,016 ns/iter (+/- 203,456)                            | 154,865 ns/iter (+/- 3,209)                     | 240,677 ns/iter (+/- 1,701)
 parallel build  | 1,213,603 ns/iter (+/- 16,978)                         | 333,477 ns/iter (+/- 6,368)                     | 9,615,379 ns/iter (+/- 236,040)                            | 1,219,772 ns/iter (+/- 49,946)                     | 1,856,047 ns/iter (+/- 18,668)
 parallel update | 3,215,346 ns/iter (+/- 34,497)                        | 41,530 ns/iter (+/- 872)                    | 6,012,745 ns/iter (+/- 604,470)                           | 333,553 ns/iter (+/- 10,704)                    | 471,636 ns/iter (+/- 20,050)

### pos_vel
 * 1000 entities with `position` and `velocity` components
 * 9000 entities with `position` components only
 * stub `render` system
 * `physics` system: `position += velocity`

### parallel
 * 10000 entities with 3 simple components `R`, `W1` and `W2`
 * `w1` system reads `R` and writes to `W1`
 * `w2` system reads `R` and writes to `W2`
 * systems could be run in parallel
