# Yakka

## Overview
Yakka is a declarative, data-focused, multi-purpose build tool.
It is designed to accomodate the complexities of embedded software development but is also suitable for all software development.

Yakkas data-focused approach is unique in comparison to other build systems such as Make which is a task based builder, or Bazel which is an artifact based builder.


## Features

- Multi-platform support for Linux, macOS, Windows
- Supports any language and tool
- Human readable syntax
- Data first and declarative
- Supports dynamic dependencies

## Basics

Every instatiation of Yakka requires arguments that indicate what actions the tool is to accomplish. This is called the "build string" and includes a combination of "commands", "components", and "features" which can appear in any order 

Example:
> `\> yakka link! my_app my_board gcc_arm`

In the example above, `link!` is a command as indicated by the trailing exclamation mark, `my_app`, `my_board`, and `gcc_arm` are all components. This example would compile and link an application for a particular platform using GCC for ARM.

Yakka everything is a component and there is no differentiation between components apart from their content.

## Next steps

Make your first component by following the [getting started guide](tutorials/getting_started.md)

To look under the hood and see how Yakka works refer to the [technical reference documentation](technical/technical_introduction.md)

## Why "Yakka"?

Derived from the Yagara language of the Indigenous people of Queensland, “yakka” refers to work or labor. It is often used to describe physical or manual tasks that require effort and exertion.
Today, “yakka” embodies not only hard work but also represents perseverance, strength, and dedication to getting the job done. It highlights the core values deeply ingrained in Australian culture.
([source](https://slangsensei.com/yakka-australian-slang/))
