# How to contribute

I'm really glad you're reading this, because that means you enjoy my stuff to an extend, where you want to engage.

## Testing

I personally try to ensure high quality content which means I test my roles against a set of operating systems. I appreciate if you do the same, but if you do not have the time or your contribution targets only one operating system just let me know and I will do the quality assurance for you if possible.

## Submitting changes

I do not require elaborate formatting of PRs, please just make sure I can understand what you did or what you intend to change. Please follow the coding conventions (below) and make sure all of your commits are atomic (one feature per commit).

Always write a clear log message for your commits. One-line messages are fine for small changes, but bigger changes should look like this:

    $ git commit -m "A brief summary of the commit
    > 
    > A paragraph describing what changed and its impact."

## Coding conventions

Start reading the code and you'll get the hang of it quite quickly.
I try to stick to Ansible and YAML conventions to the best of my knowledge.
I do appreciate if you use `yamllint` and `ansible-lint` to ensure proper linting. My repository contains configuration files for that.
Additionally I keep the code clean and readable by following some simple guidelines:

  * Task names are enclosed by double quotation marks (`""`) and end with a period (`.`)
  * Truthy values are enclosed by single  quotation marks (`''`)
  * This is open source software. Consider the people who will read your code, and make it look nice for them. It's sort of like flying a plane: Perhaps you love doing loops when you're alone, but with passengers the goal is to make the flight as smooth as possible.

Thanks for your contribution!
