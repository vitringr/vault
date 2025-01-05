---
context:
  - "[[Vim]]"
  - "[[NeoVim]]"
---

#wip

# Vim Guide

A guide to learn Vim (and maybe NeoVim) from scratch.

## Why Learn Vim?

Because it's amazing!

Vim is objectively better than the "normal" way of writing in almost every aspect.

## Who Is This For?

Anyone who wants to write and edit text much more efficiently.

Ideal for all kinds of writers and especially programmers.

## Warning

The beginning may feel unintuitive at first. It will be difficult to let go of old habits in order to learn better ones.

That's okay! It's totally normal.

Know that once you are past the Vim event horizon, you would never want to go back.

## Skill Roadmap

**None**: It will be a mess at first. Sorry.

**Beginner**: You will be as fast with Vim as you were before using it. You will know the fundamental features, and you will start to understand the intuitive design of the system.

**Intermediate**: You will be very used to the fundamental features, and you will be aware of some of the more advanced features. You will be much more efficient than before, but there's still room for improvement.

**Advanced**: Absolute flow and efficiency. There is no going back.

**Expert**: Mastery. This guide is not the place for you.

## FAQ

### General Questions

_**"Is it free and open-source?"**:_ Yes, yes.

_**"Is Vim a system or a software?"**:_ Both. As a system, Vim refers to the broader design and philosophy, and how you use it. The vim system is available for many different software programs, including _vi_, _vim_, _neovim_, and almost every other text editor out there.

_**"Can I use Vim in my code editor?"**:_ Yes! You can use vim in _VS Code_, _JetBrains_, _Sublime Text_, _Obsidian_, _..._, you name it, as well as editors specifically designed around vim, such as _NeoVim_.

### NeoVim Questions

_**What's NeoVim?**:_ It's a hyperextensible Vim-based text editor. You can read more about it on it's [Website](https://neovim.io/) or [Github Page](https://github.com/neovim/neovim). It's fast as fuck, terminal-based, fully configurable (so much that it can act as a standalone IDE), and my personal editor/IDE of choice.

_**Should I use NeoVim?**:_ Your choice. Personally I would always recommend it. Although if you are just starting with Vim you may stick to using it in your favorite code editor until you get more used to it. Or just switch to NeoVim nonetheless and commit fully. I've seen both methods work.

_**Can NeoVim be used as an IDE?**:_ Yes. The open-source community and ecosystem are big enough (and growing) to provide everything you might expect from an IDE. Features such as autocompletion, code snippets, syntax highlighting, file management, software integration, language-specific features, mass editing... it's all there.

_**Is NeoVim performant?**:_: Yes. Extremely. At the time of writing this, it took my _NeoVim_ `64.85ms` to open with everything loaded and ready. Unless you somehow try to bloat it heavily, its performance should be close to your system terminal.

### Customization Questions

_**"Can I customize Vim?"**:_ Yes. You can mold it into whatever suits you.

_**"Do I have to?"**:_ No, not necessarily. You can just use it out of the box.

My personal customization is very minimal, meaning that I can use Vim on a new machine without any prerequisites. The few keymaps and settings that I find useful will be covered in this guide.

_**How do I customize it?**:_ You have a small config file with all the settings and keymaps that you need. That's basically it.

### Skeptic Questions

_**"But why is it so hard to learn?"**:_ It's really not. The challenging part is not learning Vim itself, it's unlearning the old way.

_**"It doesn't feel intuitive for me compared to writing normally!"**:_ Most people already know how to write "normally", so they are biased towards that one familiar thing. Having done only one thing for 10-20-30 years can make it seem much more "intuitive" than it really is.

_**"Only Vim users claim that Vim is intuitive!"**:_ Well... obviously.

_**"Why is there an effort in learning Vim, then, but not normal way?"**:_ You did need to spend time and effort in learning the normal way, though. Maybe it was so long ago that you don't remember it? I'm pretty sure a child could not just start writing on a keyboard from the get-go.

_**"But it takes tiiimeee... and efffooort..."**:_ Yeah, most good things do. However, I'd argue that you will actually spend less time and effort by the end of the year if you have learned Vim. What it costs in initial time and effort will be paid back in efficiency.

_**"The Vim community is cult-ish about it."**:_ Yeah, some are. But I don't like that, and they don't need to be. Vim is only a tool - find me a better tool and I'll switch to it instead. For me, the reason for this cult-like behavior is that when you get used to Vim it's sooo much better than the "normal" way that you kind of can't help to feel stupid about not using it earlier. Naturally, when you come across something great, you may find yourself pitching it to other people.

## Beginner Guide

#wip

Beginner guide and setup.

Targeted for the first ~month of learning Vim.

**Invest Some Time**:
At the very beginning, you will be less efficient due to your old habits. But after a short amount of time, Vim will start really paying off!

I suggest investing about two weeks (maybe less) into writing with Vim. It personally took me ~10 days to start writing normally again. From this point onward, everything got better and better.

**Arrow Keys**:
Probably the most difficult challenge for beginners is to stop using the arrow keys. You should learn to always use the Vim arrows `h j k l` in normal mode instead.

You can remove/disable the arrow keys from your keyboard. It may sound a bit radical, but I'm sure it will actually save more time and struggle compared to intuitively reverting to using them. By using Vim, you wouldn’t ever need them anyway.

Using `h j k l` is nice because it will also get you used to switching to normal mode quickly.

**Hand Placement**:
Your hands should be placed in a typewriter-like way on the keyboard: left hand around `W A S D` as if you're gaming, and right hand on `J K L`.

Proper hand placement is key for speed and ergonomics. Once you get used to it, you will realize how efficient it is. Since you don't need things like the arrow keys or numpad, there will be no reason for your right hand to ever go there anyway.

You will also find that everything is where you need it. The most common operations are often placed on the closest keys by design.

**Caps Lock Button**:
You can remap your `Caps Lock` button to something else, for example `Ctrl`.

The reasoning is that you wouldn’t use the default `Caps Lock` behavior anyway, and it is really comfortable to have `Ctrl` on a better button.

The `Ctrl` key is used for various operations, especially in _NeoVim_. One of my most used operations is `Ctrl+C`, which exits insert mode. There are other ways to exit insert mode (for example, the `Esc` key), but I find `Ctrl+C` to be the fastest and most ergonomic option when your `Ctrl` is bound to the `Caps Lock` key.

## Intermediate Guide

#wip

Intermediate guide.

Targeted for after the first ~month, or after you're as fast with Vim as you were before it.

## Advanced Guide

#wip

Advanced guide and optimization.

Targeted for people who think that being twice as fast isn't as good as being three times as fast.
