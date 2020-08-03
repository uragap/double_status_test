## Quotes from the teams
Of course we can't cover every change that has happened. So we reached out and
asked some of our teams what changes they are most proud of:

> For rustdoc, the big things were:
> * The automatically generated documentation for blanket implementations
> * The search itself and its optimizations (last one being to convert it into JSON)
> * The possibility to test more accurately doc code blocks "compile_fail,
>   should_panic, allow_fail"
> * Doc tests are now generated as their own seperate binaries.
>
> — Guillaume Gomez ([rustdoc])


> Rust now has baseline IDE support! Between IntelliJ Rust, RLS and
> rust-analyzer, I feel that most users should be able to find "not horrible"
> experience for their editor of choice. Five years ago, "writing Rust" meant
> using old school Vim/Emacs setup.
>
> — Aleksey Kladov ([IDEs and editors][ides])


> For me that would be: Adding first class support for popular embedded
> architectures and achieving a striving ecosystem to make micro controller
> development with Rust an easy and safe, yet fun experience.
>
> — Daniel Egger ([Embedded WG][ewg])


> The release team has only been around since (roughly) early 2018, but even in
> that time, we've landed ~40000 commits just in rust-lang/rust without any
> significant regressions in stable.
>
> Considering how quickly we're improving the compiler and standard libraries, I
> think that's really impressive (though of course the release team is not the
> sole contributor here). Overall, I've found that the release team has done an
> excellent job of managing to scale to the increasing traffic on issue
> trackers, PRs being filed, etc.
>
> — Mark Rousskov ([Release][release])


> Within the last 3 years we managed to turn [Miri][miri-repo] from an experimental
> interpreter into a practical tool for exploring language design and finding
> bugs in real code—a great combination of PL theory and practice.  On the
> theoretical side we have [Stacked Borrows], the most concrete proposal for a
> Rust aliasing model so far. On the practical side, while initially only a
> few key libraries were checked in Miri by us, recently we saw a great uptake
> of people using Miri to [find and fix bugs] in their own crates and
> dependencies, and a similar uptake in contributors improving Miri e.g. by
> adding support for file system access, unwinding, and concurrency.
>
> — Ralf Jung ([Miri])

[miri-repo]: https://github.com/rust-lang/miri
[stacked borrows]: https://github.com/rust-lang/unsafe-code-guidelines/blob/master/wip/stacked-borrows.md
[find and fix bugs]:  https://github.com/rust-lang/miri/#bugs-found-by-miri

> If I had to pick one thing I'm most proud of, it was the work on non-lexical
> lifetimes (NLL). It's not only because I think it made a big difference in
> the usability of Rust, but also because of the way that we implemented it by
> forming the NLL working group. This working group brought in a lot of great
> contributors, many of whom are still working on the compiler today. Open
> source at its best!
>
> — Niko Matsakis ([Language])
