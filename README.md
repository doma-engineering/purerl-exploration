# purerl-exploration

## Installation

Installation requires Erlang, PureScript, Spago.
Install Erlang first because while doing so, all the system packages will be installed too.

### Erlang

Given that we are using cutting edge stack, we also prefer to use cutting-edge Erlang.
For this we are using a `.deb` file by Erlang Solutions.
Currently, we're using R24.0.5.

```
wget
https://packages.erlang-solutions.com/erlang/debian/pool/esl-erlang_24.0.5-1~ubuntu~focal_amd64.deb -O /tmp/erl.deb
sudo apt install libncurses5 libwxbase3.0-dev libwxgtk3.0-gtk3-dev libsctp1
sudo dpkg -i /tmp/erl.deb
rm /tmp/erl.deb
```

### PureScript

We need purescript compiler, which is the parent to `purerl`. Since we
piggy-back id3as framework for making PureScript applications, we use
the compiler, which is currently supported by their packages.

At the time of this commit, the compiler is v0.14.3. Corresponding
purerl compiler can be seen in [this table](https://github.com/purerl/purerl#versions).

```
wget https://github.com/purescript/purescript/releases/download/v0.14.3/linux64.tar.gz
tar xzvf linux64.tar.gz
cp purescript/purs ~/.local/bin/
rm -rvf ./linux64.tar.gz ./purescript/
```
### Spago

To automate Erlang code generation, `spago` is used.

```
wget https://github.com/purescript/spago/releases/download/0.20.3/Linux.tar.gz
tar xzvf Linux.tar.gz
mv spago ~/.local/bin
rm Linux.tar.gz
```

### Purerl

To determine the version, see "PureScript" section of this README.

At the time of writing we use purs v0.14.3 and purerl v0.0.11.

```
wget https://github.com/purerl/purerl/releases/download/v0.0.11/linux64.tar.gz
tar xzvf linux64.tar.gz
cp purerl/purerl ~/.local/bin/
purerl --version
rm -rvf linux64.tar.gz purerl/
```

### VSCode

1. Install purescript IDE extension
2. Add the following to your config:
```
    "purescript.codegenTargets": [
        "purerl"
    ]
```


## Testing it all works

Now clone something like `id3as/purescript-erl-stetson`, build it with `make ci`

## Ideal way to test that it all works

Purerl has a nice onboarding experience, a project called `demo_ps`.
Let's make sure that our stack works.

```
git clone https://github.com/id3as/demo-ps.git
cd demo-ps
rebar3 compile
```

But sadly, at the moment of writing, it's in process of getting updated to work with id3as stack 2.0.
You can track the progress of this update [here](https://github.com/robashton/demo-ps/tree/2.0).

## Purerl ideas

Check out [these repositories](https://github.com/id3as) to see libraries to help you do stuff with purerl.
