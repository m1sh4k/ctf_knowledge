##### bash execute multiply commands in one line
```bash
command1; command2
command1 | command2
command1 && command2
```
#####  bash command injection
```bash
`ur_commands_here`
$(ur_commands_here)
```

##### execute password-required comman in 1 line
```bash
echo "password" | sudo -S apt update
```