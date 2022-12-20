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

# For Windows(PowerShell)
Based on above config, just add below code into your PowerShell config file, eg: `Microsoft.PowerShell_profile.ps1`

```powershell
function auto_jump {
    $autojump_script_path = (cd ~ && $pwd.path) + "\AppData\Local\autojump\bin\autojump"

    $args = $args | Out-String
    if (-not $args.StartsWith('-') )
    {
        $new_path=(python $autojump_script_path $args)
        if (Test-Path $new_path)
        {
            cd $new_path
        } 
        else
        {
            echo autojump: directory $args not found
            echo try `autojump --help` for more information
        }
    }
    else{
        python "$pwd\autojump" $args
    }

}
Set-Alias j        auto_jump
Set-Alias autojump auto_jump
```

then you can use `autojump` or `j` in PowerShell
