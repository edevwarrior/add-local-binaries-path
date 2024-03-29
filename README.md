# add-local-binaries-path

Never type `./node_modules/.bin` again!

Make locally-installed node modules executable by name by adding
`./node_modules/.bin` to the `$PATH`.

Works for bash, fish, and zsh.

## Why?

The goal of this is to avoid "works on my machine" problems.
You shouldn't really be installing most modules globally. It's best
to declare all of your project's dependencies in the package.json file, so
`npm install` will always work for everyone, regardless of what they have
installed globally.

## Installation

```sh
npm i -g add-local-binaries-path
```

A postinstall task looks for these files:

```
~/.bashrc
~/.bash_profile
~/.config/fish/config.fish
~/.zshrc
```

For each shell configuration file found, a string is injected into the file
 that adds `.node_modules/.bin` to the `$PATH` environment variable.

 For bash and zsh, it looks like this:

 ```sh
 export PATH="$PATH:./node_modules/.bin"
 ```

 For fish, this:

 ```fish
 set -gx PATH $PATH ./node_modules/.bin
 ```

## Usage

Once you've installed this module, you never really need to use it agin. It has
done its work. To make sure it's working, try this:

```sh
mkdir foo
cd foo
npm init --yes
npm i shrug --save
shrug
which shrug
```

## License

MIT
