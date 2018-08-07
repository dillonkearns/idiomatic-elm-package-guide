# Idiomatic Elm Package Guide

## Goals

The purpose of this guide is to provide you with resources to get started writing an Elm package. And to
help you write an Elm package that is:

1. Valuable.
1. Constrained to prevent impossible states.
1. Easy to learn and use.
1. Easy to tell if it's the right fit for the problem at hand.
1. Consistent with the README and documentation conventions in the Elm community.

## How to Use This Guide

Start with reading through [TEMPLATE.md](./TEMPLATE.md). Then copy-paste the raw file as a starting point for your `README.md` file.

The rest of this document provides guiding principles, tips, and resources.

Feedback through Slack, Github issues, or pull requests is always welcome! If it's not an obvious change, it might be best to hold off on the pull request until after some initial discussion around the idea to make sure we're on the same page.

## 1. Valuable

If your package isn't valuable, then the rest of these principles won't help you much! Here are some tips to maximize the value of your Elm package.

* Start simple. Introduce complexity sparingly.
* Valuable doesn't mean comprehensive. It can be a minimal, simple package but still be extremely valuable. Think of the single-purpose philosophy of unix tools like `ls` or `grep`.
* Design a [consumer-driven API](https://youtu.be/t-2GiOuLRZc?t=49m41s) (see 49:41-52:57)
* Check out [Let's Publish Nice Packages - Brian Hicks at Elm Europe 2018](https://www.youtube.com/watch?v=yVn7FOQuwDM) for some great tips like doing research on similar tools and avoiding direct ports from other libraries

### Practice `examples`-Driven Development

When writing your Elm package, try to expose the minimal interface possible, AND drive that interface by concrete use cases. Test-driven development is a great way to do this on the micro level (see [programming by intention](https://tobeagile.com/2016/08/31/programming-by-intention/)). Take a look at the [elm-test documentation](https://github.com/elm-community/elm-test) for how to get started, and for best practices on writing a test suite.

On the macro level, try starting with an `examples` folder (i.e. `examples`-Driven Development). Start with a simple yet meaningful example. (For example, with [`elm-cli-options-parser`](https://github.com/dillonkearns/elm-cli-options-parser), I started with an end-to-end example of building up the `elm-test` Command-Line Interface since it is a simple but meaningful and concrete interface). Then, add features to your package as needed to complete this simple but meaningful example and get it working fully end-to-end.

As you iterate on your design, review your `examples` folder and ask yourself some questions:

* Are you proud to show these examples off?
* Is it obvious to someone who hasn't used your library what they are doing?
* Does the public API make sense?
* Could the examples be any simpler if the API were different?
* Is it discoverable (i.e. easy to find the functions you need to accomplish a task)?
* Can you express things that are invalid using your API?

## 2. Well-Constrained

When publishing a package you will need a toolkit of advanced Elm type techniques to create a clear public API, and one that models the constraints of your library's domain. The [Official Elm API Design Guidelines](http://package.elm-lang.org/help/design-guidelines) are a good starting point.

### Make use of advanced Elm types to make a simpler API and to model the constraints of your domain better

These articles by Charlie Koster on advanced Elm types are very useful when writing Elm packages.

* [Part I - Opaque Types](https://medium.com/@ckoster22/advanced-types-in-elm-opaque-types-ec5ec3b84ed2)
* [Part II - Extensible Records](https://medium.com/@ckoster22/advanced-types-in-elm-extensible-records-67e9d804030d)
* [Part III - The Never Type](https://medium.com/@ckoster22/advanced-types-in-elm-the-never-type-ca9b3297bbd4)
* [Part IV - Phantom Types](https://medium.com/@ckoster22/advanced-types-in-elm-phantom-types-808044c5946d)

These videos are full of great tips for designing APIs.

* [Make Data Structures - Richard Feldman @ Elm Europe 2018](https://www.youtube.com/watch?v=x1FU3e0sT1I)
* [Make Impossible States Impossible](https://www.youtube.com/watch?v=IcgmSRJHu_8)
* [Understanding Style - Matthew Griffith @ Elm Europe 2017](https://www.youtube.com/watch?v=NYb2GDWMIm0) - Matt goes into details about his consumer-driven API

## 3. Easy to learn and use

See [the Learning Resources section in the README template](https://github.com/dillonkearns/idiomatic-elm-package-guide/blob/master/TEMPLATE.md#learning-resources).

Here are some examples of learning sections from Elm package READMEs:

* [Style Elements learning section](https://github.com/mdgriffith/style-elements/tree/9c36d062f55e0a2b32e5b0158037ed8ff91adcd7#resources-to-get-you-started)
* [Graphqelm learning section](https://github.com/dillonkearns/graphqelm#learning-resources)

### `CHANGELOG.md`

Maintain a file called `CHANGELOG.md` in the root folder of your project on Github. The purpose of this is to make it easy for users to

* Learn about new features (and how to use them)
* Learn how to upgrade to new major versions
* See when a bug is fixed

This is more granular than the commit log itself.

Copy-paste the template from [Keep a Changelog](https://keepachangelog.com/) to get started and follow the principles stated there. It's very well thought out and easy to follow once you get going with it.

### Maintain a Frequently Asked Questions (FAQ)

Every time someone asks a question, consider answering it in your FAQ.

* Keep FAQs in an FAQ.md file or FAQ section in your README.
* Instead of directly answering a common question, send a link to the answer. That way you don't ever have to write that answer again, and it is there for future reference.
* If a question keeps coming up, it may also mean that it's an opportunity to make your API simpler or more intuitive.

## Useful Resources

Brian's talk on publishing a package
Elm package previews
Medium blog posts on publishing elm packages
Elm guide on publishing packages, making nice modules and docs
Richard's Elm Europe talk on APIs (both keynotes)
Evan's talk on the evolution of a package

## License

## Managing feature requests

## Code of conduct

## Tracking contributors

## Hiding Types for your package

Expose the minimum possible interface, and [make impossible states impossible (see this video)](Link).
Blog posts on fancy types, like opaque, phantom, etc. Use these tools to make impossible states impossib le

## Nice examples of elm packages that follow this philosophy

Remote Data
Style Elements
Graphqelm

## Resources

* [Elm Documentation Preview tool](http://package.elm-lang.org/help/docs-preview)
* [Official guide for creating Elm docs](http://package.elm-lang.org/help/documentation-format)

## _TODO_

* [ ] Badge for this site
