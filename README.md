# git-walk - walk a directory tree, executing command in every git repo

## Usage

```
usage: git-walk [-vq1n] [-w WHERE] [-n CONCURRENCY] [-- command]

Run `command` in every git repo found. The command defaults to:

    git status --short -b

By default, the commands are run in parallel, and their stderr and stdout are
printed when the commmand completes, to avoid having the parallel command
output intermingled unintelligibly. Some commands only colorize when writing to
a terminal, in which case --serial may be useful, which runs the command with
output directly to the console at the price of being slower.

Options:
  -h,--help       Print this helpful message and exit.
  -v,--verbose    Print commands that are being run (the default).
  -q,--quiet      Do not print commands that are being run.
  -w,--where=W    Look for git repos in `W` and below.
  -1,--serial     Run serially.
  -p,--parallel   Run commands in parallel (the default).
  -n CONCURRENCY  Run this many commmands in parallel (default is 20).

Examples:

    git-walk -p -q -- git describe
    git-walk -- git fetch --prune --all
    git-walk -- git co master
```

## License

MIT
