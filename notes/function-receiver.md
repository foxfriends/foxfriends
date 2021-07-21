# Method Receiver

The __receiver__ of a @[method][] is the value on which the @[function][] is called
(e.g. the `this` or `self` value of that function).

In @[languages][programming-language] with the usual method call syntax, the receiver is the value
to the left of the `.`. In some languages (@[Javascript][], @[Java][], @[C++][cplusplus]), the receiver
is passed implicitly to the function, while in others (@[Rust][], @[Go][go-language]), the receiver is declared
explicitly. This difference is typically due to the differences in how methods are defined.
