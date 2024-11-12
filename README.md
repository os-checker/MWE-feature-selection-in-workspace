
* 类似的问题像这个：<https://github.com/rust-lang/cargo/issues/4463>
* 9月合并了相关的 RFC 来解决类似的问题 <https://github.com/rust-lang/rfcs/pull/3692>

```shell
$ cargo c
error[E0635]: unknown feature `read_initializer`
 --> /root/.cargo/registry/src/rsproxy.cn-0dccff568467c15b/core2-0.4.0/src/lib.rs:3:64
  |
3 | #![cfg_attr(all(feature = "std", feature = "nightly"), feature(read_initializer))]
  |                                                                ^^^^^^^^^^^^^^^^
```

```shell
$ cargo c -p test-core2-member1 # compiles
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.09s

$ cargo c -p test-core2-member2 # compiles
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 5.16s

# same as follows

$ cd test-core2-member1 && cargo c # compiles
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.02s

$ cd test-core2-member2 && cargo c # compiles
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.03s
```


