<details>
 <summary>1.43.0 Error Message</summary>

```
   Compiling error-messages v0.1.0 (/Users/ep/src/rust/error-messages)
error[E0277]: the size for values of type `dyn std::io::Write` cannot be known at compilation time
 --> src/lib.rs:6:13
  |
6 |     generic(w);
  |             ^ doesn't have a size known at compile-time
...
9 | fn generic<W: Write>(_w: &W) {}
  |    ------- -       - help: consider relaxing the implicit `Sized` restriction: `+  ?Sized`
  |            |
  |            required by this bound in `generic`
  |
  = help: the trait `std::marker::Sized` is not implemented for `dyn std::io::Write`
  = note: to learn more, visit <https://doc.rust-lang.org/book/ch19-04-advanced-types.html#dynamically-sized-types-and-the-sized-trait>

error: aborting due to previous error

For more information about this error, try `rustc --explain E0277`.
error: could not compile `error-messages`.

To learn more, run the command again with --verbose.
```

</details>

![A terminal screenshot of the 1.43.0 error message.][trait-error-1.43.0]
