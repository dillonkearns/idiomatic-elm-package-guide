# Idiomatic Elm Package Guide

## Goals/Table of Contents

The purpose of this guide is to provide you with [resources to get started writing an Elm package](#learning-resources). And to
help you write an Elm package that is:

1. [Valuable](#1-valuable)
1. [Constrained to prevent impossible states](#2-well-constrained)
1. [Easy to learn and use](#3-easy-to-learn-and-use)
1. [Easy to tell if it's the right fit for the problem at hand](#4-easy-to-tell-if-its-the-right-fit-for-the-problem-at-hand)
1. [Consistent with the README and documentation conventions in the Elm community](#5-consistent-with-the-readme-and-documentation-conventions-in-the-elm-community)

## How to Use This Guide

Start with reading through [TEMPLATE.md](./TEMPLATE.md). Then copy-paste the raw file as a starting point for your `README.md` file.

The rest of this document provides guiding principles, tips, and resources.

Feedback through Slack, Github issues, or pull requests is always welcome! If it's not an obvious change, it might be best to hold off on the pull request until after some initial discussion around the idea to make sure we're on the same page.

## Learning Resources

### The Basics

- The [Elm Package Documentation](https://github.com/elm-lang/elm-package) has basic information on publishing a package, and a few design guidelines
- [Elm Documentation Preview tool](http://package.elm-lang.org/help/docs-preview) is how you see your docs locally before publishing your package.
- [Official guide for creating Elm docs](http://package.elm-lang.org/help/documentation-format)

Here are a couple of blog posts on the basics of publishing an Elm package:

- [Publishing Your First Elm Package - @billperegoy](https://becoming-functional.com/publishing-your-first-elm-package-13d984a1200a)
- [How to publish an Elm package - @Max_Goldstein](https://medium.com/@Max_Goldstein/how-to-publish-an-elm-package-3053b771e545)

# Core Principles

## 1. Valuable

If your package isn't valuable, then the rest of these principles won't help you much! Here are some tips to maximize the value of your Elm package.

- Start simple. Introduce complexity sparingly.
- Valuable doesn't mean comprehensive. It can be a minimal, simple package but still be extremely valuable. Think of the single-purpose philosophy of unix tools like `ls` or `grep`.
- Design a [consumer-driven API](https://youtu.be/t-2GiOuLRZc?t=49m41s) (see 49:41-52:57)
- Check out [Let's Publish Nice Packages - Brian Hicks at Elm Europe 2018](https://www.youtube.com/watch?v=yVn7FOQuwDM) for some great tips like doing research on similar tools and avoiding direct ports from other libraries

### Practice `examples`-Driven Development

When writing your Elm package, try to expose the minimal interface possible, AND drive that interface by concrete use cases. Test-driven development is a great way to do this on the micro level (see [programming by intention](https://tobeagile.com/2016/08/31/programming-by-intention/)). Take a look at the [elm-test documentation](https://github.com/elm-community/elm-test) for how to get started, and for best practices on writing a test suite.

On the macro level, try starting with an `examples` folder (i.e. `examples`-Driven Development). Start with a simple yet meaningful example. (For example, with [`elm-cli-options-parser`](https://github.com/dillonkearns/elm-cli-options-parser), I started with an end-to-end example of building up the `elm-test` Command-Line Interface since it is a simple but meaningful and concrete interface). Then, add features to your package as needed to complete this simple but meaningful example and get it working fully end-to-end.

As you iterate on your design, review your `examples` folder and ask yourself some questions:

- Are you proud to show these examples off?
- Is it obvious to someone who hasn't used your library what they are doing?
- Does the public API make sense?
- Could the examples be any simpler if the API were different?
- Is it discoverable (i.e. easy to find the functions you need to accomplish a task)?
- Can you express things that are invalid using your API?

## 2. Well-Constrained

When publishing a package you will need a toolkit of advanced Elm type techniques to create a clear public API, and one that models the constraints of your library's domain. The [Official Elm API Design Guidelines](http://package.elm-lang.org/help/design-guidelines) are a good starting point.

### Make use of advanced Elm types to make a simpler API and to model the constraints of your domain better

These articles by Charlie Koster on advanced Elm types are very useful when writing Elm packages.

- [Part I - Opaque Types](https://medium.com/@ckoster22/advanced-types-in-elm-opaque-types-ec5ec3b84ed2)
- [Part II - Extensible Records](https://medium.com/@ckoster22/advanced-types-in-elm-extensible-records-67e9d804030d)
- [Part III - The Never Type](https://medium.com/@ckoster22/advanced-types-in-elm-the-never-type-ca9b3297bbd4)
- [Part IV - Phantom Types](https://medium.com/@ckoster22/advanced-types-in-elm-phantom-types-808044c5946d)

These videos are full of great tips for designing APIs.

- [Make Data Structures - Richard Feldman @ Elm Europe 2018](https://www.youtube.com/watch?v=x1FU3e0sT1I)
- [Make Impossible States Impossible](https://www.youtube.com/watch?v=IcgmSRJHu_8)
- [Understanding Style - Matthew Griffith @ Elm Europe 2017](https://www.youtube.com/watch?v=NYb2GDWMIm0) - Matt goes into details about his consumer-driven API

## 3. Easy to learn and use

### Use the ["Inverted Pyramid"](<https://en.wikipedia.org/wiki/Inverted_pyramid_(journalism)>)

You need a hook that let's potential users know whether it's worth their time
to read more about your package or try it out. So give very clear summaries
at the top that include key points. You can use this basic inverted pyarmid
structure from journalism (i.e. bottom line up front... however far you
read, you've read the most important points).

1. Key summary
   - Headline (the github project description... this is the first thing users see)
   - Why would I want to use this over other packages?
   - What problem does it solve?
2. Important details

   - How do I install and use this library?

3. Other background information
   - Advanced usage tips

### Use [Ubiquitous Domain Language](https://martinfowler.com/bliki/UbiquitousLanguage.html)

Use the same language everywhere, whether it's in a doc comment,
the README, an example folder, an exposed function name or type, a type variable name
(yes, even type variables, they show up in the docs, so they deserve great names, too!).
And even your internal code! Bad naming in the internals of your code will
inevitably leak out into confusing names that are public facing.

With that said, recognize that [naming is a process](http://arlobelshee.com/good-naming-is-a-process-not-a-single-step/).
Don't expect to have the perfect names mapped out in your first commit. Iterate
on the naming, just be sure to relentlessly do renaming refactors and module
extracts as you see the opportunity for more clear names.

### Learning Resources

See [the Learning Resources section in the README template](https://github.com/dillonkearns/idiomatic-elm-package-guide/blob/master/TEMPLATE.md#learning-resources).

Here are some examples of learning sections from Elm package READMEs:

- [Style Elements learning section](https://github.com/mdgriffith/style-elements/tree/9c36d062f55e0a2b32e5b0158037ed8ff91adcd7#resources-to-get-you-started)
- [`dillonkearns/elm-graphql` learning section](https://github.com/dillonkearns/elm-graphql#learning-resources)

### `CHANGELOG.md`

Maintain a file called `CHANGELOG.md` in the root folder of your project on Github. The purpose of this is to make it easy for users to

- Learn about new features (and how to use them)
- Learn how to upgrade to new major versions
- See when a bug is fixed

This is more granular than the commit log itself.

Copy-paste the template from [Keep a Changelog](https://keepachangelog.com/) to get started and follow the principles stated there. It's very well thought out and easy to follow once you get going with it.

### Maintain a Frequently Asked Questions (FAQ)

Every time someone asks a question, consider answering it in your FAQ.

- Keep FAQs in an FAQ.md file or FAQ section in your README.
- Instead of directly answering a common question, send a link to the answer. That way you don't ever have to write that answer again, and it is there for future reference.
- If a question keeps coming up, it may also mean that it's an opportunity to make your API simpler or more intuitive.

### Always expose types that can be created from your API

You often see Github issues or pull requests [like this one](https://github.com/mdgriffith/style-elements/pull/95) requesting that [an Opaque Type](https://medium.com/@ckoster22/advanced-types-in-elm-opaque-types-ec5ec3b84ed2) be exposed in the API so that users of the API can annotate their functions that use values of that type. Avoid these types of requests by always following this rule of thumb:

> If your public API allows you to create a value (even an intermediary one) of a given type, _always_ expose that type in your public API so users can annotate their functions.

## 4. Easy to tell if it's the right fit for the problem at hand

### Explicitly State Design Goals in Your README

What differentiates your project from any other project out there? Since Elm packages are reliable due to the nature of the elm language and its guarantees, what makes Elm packages stick out more is not its reliability, but its design philosophy. So we put the design philosophy as the first section after the initial introduction.

Writing out explicit design goals is a great idea even before you write any code (of course you can always revise them). They serve as:

- A reminder to the package author of the core principles during design iteration
- A clear statement of goals to help users decide whether the library is a good fit for them
- A reference point for conversations about feature requests that helps ground the conversation in the basic goals of the library. This makes for a much more empathetic conversation (for example, someone could have a great idea that's not inline with the design goals of a library... in that case, perhaps a new library could be created, OR a different solution could be considered that honors the design goals of the library)

Here are some examples of design goals clearly stated in an Elm package README:

- [`dillonkearns/elm-graphql` design goals](https://github.com/dillonkearns/elm-graphql#dillonkearnselm-graphql)
- [Style Elements design goals](https://github.com/mdgriffith/style-elements/#building-a-new-layout-language)

See [the Design Goals section of the README template](https://github.com/dillonkearns/idiomatic-elm-package-guide/blob/master/TEMPLATE.md#design-goals).

## 5. Consistent with the README and documentation conventions in the Elm community

You can use this template as a starting point. See the [How to Use This Guide](https://github.com/dillonkearns/idiomatic-elm-package-guide#how-to-use-this-guide) section of this README!

Here are some examples of packages that you can use as inspiration:

- [`elm-test`](https://github.com/elm-community/elm-test)
- [`mdgriffith/style-elements`](https://github.com/mdgriffith/style-elements/)
- [`dillonkearns/elm-graphql`](https://github.com/dillonkearns/elm-graphql)

### Put a Headline and Elm Package link in the Github Project description

If you click edit up at the top-right of your github page, you'll have
a place to enter a `Description` and `Website`. Put a link to your project's
Elm package page in the `Website`.
In the `Description`, put a catchy headline that summarizes what your library
does and what makes it unique in a short sentence.

For example, for [`mdgriffith/style-elements`](https://github.com/mdgriffith/style-elements/)
it is:

`Description`: Create styles that don't mysteriously break!
`Website`: https://package.elm-lang.org/packages/mdgriffith/style-elements/latest

### License

The [recommended license for Elm projects is BSD3](https://github.com/elm-lang/elm-package#preparing-for-publication).

### Package Naming

- The Elm community encourages that package authors follow its [Literal Naming Policy](https://discourse.elm-lang.org/t/literal-names-policy-i-e-how-to-name-packages/242).

- The Elm core team recommends that you "use the `elm-` prefix unless `elm` already appears in the repository name".
