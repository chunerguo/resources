# Bash cheatsheet  

My personal cheat sheet for common bash commands  

## Navigating directories
```
ls                        # List directories
ls -a                     # List directories including hidden
ls -l                     # List directories in long form
ls -lh                    # List directories in long human readable form
cd                        # Go to home directory
cd ~                      # Go to home directory
cd foo                    # Go to foo sub-directory
cd -                      # Go to last directory
```

## Quick look within directories  
```
tree                      # List directory and file tree
tree -a                   # List directory and file tree including hidden
tree -d                   # List directory-only tree
du -sh *                  # Summarize directory size in human readable form
```

## Create, copy, move, delete  
```
mkdir foo                 # Create a directory
mkdir foo bar             # Create multiple directories
cp foo.txt bar.txt        # Copy file
cp -r                     # Copy directory
mv foo.txt bar.txt        # Move file
mv foo bar                # Move directory
rmdir foo                 # Delete empty directory
rm foo.txt                # Delete file
rm -r                     # Delete directory including contents
rm -rf                    # Delete directory including contents, ignore nonexistent files and never prompt
```