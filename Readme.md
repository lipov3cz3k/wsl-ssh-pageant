# wsl-ssh-pageant

[![Build status](https://ci.appveyor.com/api/projects/status/wybb41qnokuwj7a4?svg=true)](https://ci.appveyor.com/project/lipov3cz3k/wsl-ssh-pageant)

## How to use with WSL

1. On the Windows side run Pageant (or compatible agent such as gpg4win).

2. Run `wsl-ssh-pageant.exe --wsl C:\wsl-ssh-pageant\ssh-agent.sock` (or any other path) on windows in a short path (max ~100 characters total!)

3. In WSL run the following

```
$ export SSH_AUTH_SOCK=/mnt/your-path-to-wsl-ssh-pageant.exe/ssh-agent.sock
```
For example, if you have wsl-ssh-pageant.exe in `C:\wsl-ssh-pageant`
```
$ export SSH_AUTH_SOCK=/mnt/c/wsl-ssh-pageant/ssh-agent.sock
```

4. The SSH keys from Pageant should now be usable by `ssh`!

## How to use with Windows 10 native OpenSSH client

1. On the Windows side run Pageant (or compatible agent such as gpg4win).

2. Run `wsl-ssh-pageant.exe --winssh ssh-pageant` (or any other name) on windows in a short path (max ~100 characters total!)

3. In cmd.exe run the following (or define it in your Environment Variables on windows)

```
$ set SSH_AUTH_SOCK=\\.\pipe\ssh-pageant
```
(or whichever name you gave the pipe)

4. The SSH keys from Pageant should now be usable by `ssh`!

## Note

You can use both `--winssh` and `--wsl` parameters at the same time with the same process to proxy for both

## Credit
Original author is [Doridian](https://github.com/Doridian/wsl-ssh-pageant) who integrated windows ssh to wsl-ssl-pageant created by [benpye](https://github.com/benpye/wsl-ssh-pageant).
In this fork I add appveyor integration originaly written by [tprasadtp](https://github.com/tprasadtp/pipe-ssh-pageant) in his separated project.

Thanks to [John Starks](https://github.com/jstarks/) for [npiperelay](https://github.com/jstarks/npiperelay/), showing a more secure way to create a stream between WSL and Linux.
