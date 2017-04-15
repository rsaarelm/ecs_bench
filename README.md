# Benchmarks of various Rust Entity Component Systems

## Benchmarks
Benchmarks are run on [Travis CI](https://travis-ci.org/lschmierer/ecs_bench/).

Benchmarks are located in `benches/[bench_name]_[ecs_crate_name].rs`.

 Benchmark       | [ecs](https://github.com/HeroesGrave/ecs-rs) | [specs](https://github.com/slide-rs/specs) | [recs](https://github.com/andybarron/rustic-ecs) | [trex](https://github.com/rcolinray/trex) | [calx-ecs](https://github.com/rsaarelm/calx-ecs) | [froggy](https://github.com/kvark/froggy)
 --------------- |:--------------------------------------------:|:------------------------------------------:|:------------------------------------------------:|:-----------------------------------------:|:------------------------------------------------:|:-----------------------------------------:
 pos_vel build   | 991,695 ns/iter (+/- 17,799)                          | 235,517 ns/iter (+/- 52,036)                      | 7,813,456 ns/iter (+/- 473,549)                             | 664,628 ns/iter (+/- 8,484)                      | 206,398 ns/iter (+/- 4,682)                         | 620,132 ns/iter (+/- 5,487)
 pos_vel update  | 216,728 ns/iter (+/- 2,098)                         | 28,770 ns/iter (+/- 1,162)                     | 2,372,784 ns/iter (+/- 380,228)                            | 154,918 ns/iter (+/- 9,695)                     | 13,046 ns/iter (+/- 115)                        | 10,759 ns/iter (+/- 102)
 parallel build  | 982,179 ns/iter (+/- 100,251)                         | 353,151 ns/iter (+/- 149,879)                     | 10,253,117 ns/iter (+/- 553,443)                            | 1,214,910 ns/iter (+/- 89,723)                     | 304,375 ns/iter (+/- 17,637)                        | 1,490,122 ns/iter (+/- 4,531)
 parallel update | 2,511,966 ns/iter (+/- 140,465)                        | 46,536 ns/iter (+/- 23,618)                    | 6,694,560 ns/iter (+/- 4,141,954)                           | 333,699 ns/iter (+/- 10,161)                    | 53,196 ns/iter (+/- 547)                       | 41,034 ns/iter (+/- 14,377)

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

## Notes
 * the benchmarks explore a limited subset of ECS use-cases and do not necessarily reflect the peformance of large-scale applications
 * [froggy](https://github.com/kvark/froggy) is technically not an ECS, but a Component Graph System (CGS)
