# TailwindCSS

[Tailwind][] is a @[CSS][] framework (or really, a CSS alternative) that uses
tons of generated utility classes to remove the need for writing CSS in
favour if simply applying a bunch of classes directly to the element.

[Tailwind]: https://tailwindcss.com/

While utility class based CSS tends to be a pain to work with when you
have to write those classes manually, Tailwind does a good job of a few
things to make it much more enjoyable:
1.  The provided collection of utility classes with consistent naming and
    semantics means you don't have to think about much.
2.  The generated classes include ways to encode media queries and hover
    states, which is rarely easy with hand-written utility classes.
3.  Only classes that are actually used get output into the final site,
    so you save a lot of space.

I find that Tailwind works particularly well when paired with some sort
of @[frontend framework][frontend-frameworks], such as @[React][] or a
@[templating engine][html-templating], as the class strings tend to get long, fast.
Without a way to consistently re-use these class strings, they will end
up copy pasted everywhere, which is not ok. Though you can create your
own custom classes to handle this case, that is not ideal as you're
basically just writing a CSS file at that point, so many of the benefits
of the utility-based approach are lost.
