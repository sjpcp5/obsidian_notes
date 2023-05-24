[Deno Documentation to Install](https://deno.com/manual@v1.33.4/getting_started/installation)
install on bash terminal 
`curl -fsSL https://deno.land/x/install/install.sh | sh`

add to home bash file `~/.bashrc`
```
  export DENO_INSTALL="/home/$username$/.deno"
  export PATH="$DENO_INSTALL/bin:$PATH"

```

run `deno completions bash > ~/deno.bash`
run `source ~/deno.bash`
Doing this helps you to see subcommands and options by pressing tab a couple of times after typing `deno` in the terminal

deno  --help
