---
title: {{cookiecutter.project_title}}
author: {{cookiecutter.author}}
version: {{cookiecutter.version}}
footer: Generated from the Entangled Bootstrap template.
---

``` {.dhall .bootstrap-card-deck}
let Card = ./schema/Card.dhall

in [ Card :: { title = "Hello, World!"
             , text =
                ''
                This is a 'Hello, World' example of literate program
                with a Bootstrap skin.
                ''
             , image = Some "img/hello-world-thumb.jpg"
             , link = Some { href = "https://github.com/entangled/bootstrap"
                           , content = "GitHub page" } }

   , Card :: { title = "Cookiecutter"
             , text =
                ''
                Made with Cookiecutter.
                ''
             , image = Some "img/cookie.jpg"
             , link = Some { href = "https://cookiecutter.readthedocs.io/"
                           , content = "About Cookiecutter" } }

   , Card :: { title = "Powered by Pandoc"
             , text =
                ''
                Pandoc is the universal document converter.
                ''
             , link = Some { href = "https://pandoc.org/MANUAL.html"
                           , content = "Pandoc Manual" }
             , image = Some "img/pandoc.png" }
   ]
```

This template should get you started with writing literate programs. The idea is, that, once you have used this template (via cookiecutter), you write your code inside a set of Markdown files in the `lit` directory. This Markdown is converted to runnable code on the fly by Entangled, while Pandoc generates the HTML documentation. If you use Github, these pages can be hosted from Github Pages.

In the intended workflow you edit the Markdown for content, and the code for function. Changes in the source code are automatically fed back to the Markdown by Entangled. You can extend the `Makefile` for extra functionality and tweak the files in the `style` directory for presentation. The generated pages in `docs` are constantly being kept up-to-date by the running `Makefile`.

# Prerequisites

For some of these dependencies, being NodeJS and Pandoc, most Linux distributions ship a version that is usually a bit outdated and it is generally recommended to install them manually.

-------------------------------------------------------------------------------------------------------------
Dependency            Where to get it                     Why 
--------------------- ----------------------------------- ---------------------------------------------------
GNU Make              (system)                            Used to coordinate deployment.

Python &ge; 3.7       (system)                            Powers `entangled-filters`, and `cookiecutter`.

`tmux`                (system)                            `make watch` will start several commands in one
                                                          window.

`inotifywait`         (system)                            Waits for changes, then runs Pandoc whenever
                                                          needed.

`node`                [NodeJS](https://nodejs.org/en/)    Needed for `browser-sync`.

Pandoc                [Pandoc home](https://pandoc.org/)  Converts documents.

`dhall-to-json`       [Dhall releases](https://github.com Configuration language.
                      /dhall-lang/dhall-haskell/releases)

`cookiecutter`        `pip install cookiecutter`          Create new project to this template.

`entangled-filters`   `pip install entangled-filters`     Pandoc filters needed.

`browser-sync`        `npm install -g browser-sync`       Serves the generated page, and automatically
                                                          reloads your browser.

`entangled`           [Entangled](                        Does what Entangled does.
                      https://entangled.github.io)
-------------------------------------------------------------------------------------------------------------

# Usage

Create a new project by running cookiecutter

```bash
cookiecutter https://github.com/entangled/bootstrap
```

Watch for changes in source directories and view them in the browser

```bash
make watch
```

# Tweaking

## Makefile

The building of this page is managed by GNU Make. If you need to build your code or generate graphics this is the place to configure that.

## Style

The default Bootstrap style may not always be what you want. There is an aditional CSS file in `style/mods.css`.

## HTML Template

The template HTML is in `style/template.html`. If you prefer a different layout for the navigation, or wish to tweak the main layout in other ways, this is the place to do so.

## Upgrading 

To upgrade to the latest version of Entangled Bootstrap Cookiecutter, assuming your current working directory is the project folder

```bash
cookiecutter --replay --output-dir .. --overwrite-if-exists \
    https://github.com/entangled/bootstrap.git
```

This will overwrite existing files, so beware! If you want to recover your files:

```bash
git diff
```

and 

```bash
git checkout -- Makefile lit/index.md style/mods.css
```

are your friends. Alternatively, you may upgrade from a new/separate branch, using `meld` or `vimdiff` to merge the changes manually. Ideas are welcome on how to smoothen this process.

# Examples

- [Chaotic Pendulum](https://jhidding.github.io/chaotic-pendulum): uses **PureScript** to run a model of a chaotic pendulum in the browser.

# License

Copyright 2020 Johan Hidding, Netherlands eScience Center

> This template is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0); you may not use this file except in compliance with the License.  You may obtain a copy of the License at
> 
>     http://www.apache.org/licenses/LICENSE-2.0
>
> Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the License for the specific language governing permissions and limitations under the License.

