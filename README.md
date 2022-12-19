# For Windows(CMD)

fix issue refer from (https://github.com/wting/autojump/issues/628#issuecomment-788407391)

## Install autojump
clone or download `zip`
```shell
git clone git://github.com/wting/autojump.git
```
install autojump
```shell
python install.py
```
then add below path to `ENV Path` manually
```shell
C:\Users\<🔥user_name>\AppData\Local\autojump\bin
```

## Install autowalk
dowload `autowalk` from `pypi`
```shell
pip install autowalk
```

command `aw` can be used, and generate the default config first
```shell
aw -h 
```

change the config (with your editor that can open `"~"` in WinOS)
```shell
subl ~/.autowalk.py
```

```shell
# change config file
first: change the opetion `recursion_root_list` to yourself
	=> the default config is `WSL` file system format
	=> you can change it to Linux fs format / WinOS fs format

then : change the opetion `autojump_default_config` to yourself
	=> In WinOS: `C:/Users/<🔥user_name>/AppData/Roaming/autojump/autojump.txt`
```

## Generate autojump rules
generate `autojump` rules by `autowalk` (make sure above config is ok)
```shell
aw -a
```

list the rules
```shell
aw -l
```


finally, use `j` or `autojump` command to jump into `folder_name` that you expect
```shell
j <folder_name>
```
