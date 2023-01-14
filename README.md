# Containerized cli tools

This repo is a collection of containerized command line tools,
with the goal of hiding the fact that it's run in a container as
much as possible. The docker run command (or equivalent) would be
specified as a shell alias (or in a wrapper script).

For instance, with a built docker image called `youplot`, and an
alias in your ~/.${SHELL}rc as:

    alias uplot='docker run -i --rm youplot'

You'd be able to use the uplot command as if it was installed on
your system directly:

```
$ curl -sL https://git.io/ISLANDScsv | sort -nk2 -t, | tail -n3 |
> docker run -i --rm youplot -C bar -d, -t "Areas of the World's Major Landmasses"
                   Areas of the World's Major Landmasses
                 ┌                                        ┐
   North America ┤■■■■■■■■■■■■■■■■■ 9390.0
          Africa ┤■■■■■■■■■■■■■■■■■■■■■ 11506.0
            Asia ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 16988.0
                 └                                        ┘
```

In other cases, the alias could contain a series of volume mounts
(e.g. `-v $PWD:$PWD`), and a `-w $PWD` to make the program
believe it's executed from the same directory that you are
running the container from.
