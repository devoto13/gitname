## Gitname

Simple script to set `user.name` and `user.email` or other properties into git repository based on remote hostname or repository.


## Setup
Put `gitname.py` into your path, for example as `/usr/local/bin/gitname` or `~/.local/bin/gitname`:
```bash
curl -L https://raw.githubusercontent.com/alex-shpak/gitname/master/gitname.py > /usr/local/bin/gitname
``` 

Set executable permissions to the script:
```bash
sudo chmod +x /usr/local/bin/gitname
```

Put file `.gitname` into your home directory with content
```ini
[github.com]
user.name: Alex Shpak
user.email: alex-shpak@users.noreply.github.com

[github.com/alex-shpak/gitname.git]
user.name: Alex
```

Run script in git repository. As result local git config will be updated with matching values.  
Note that repository specific config sections has higher priority.
```
user@host:~/Projects$ cd gitrepo/
user@host:~/Projects/gitrepo$ gitname 
Set user.name "Alex Shpak"
Set user.email "alex-shpak@users.noreply.github.com"
user@host:~/Projects/gitrepo$ 
```

## Flags
```
$ python gitname.py -h
usage: gitname.py [-h] [-v] [-q] [-r REMOTE]

Updates git config based on ~/.gitname.

optional arguments:
  -h, --help            show this help message and exit
  -v, --verbose         print debugging output
  -q, --quiet           run without output
  -r REMOTE, --remote REMOTE
                        sets remote for lookup
```

## Git hook
You can setup local or global git hook for automatic run. See [git docs](https://git-scm.com/docs/githooks)


## Licence
[MIT](LICENCE.txt)