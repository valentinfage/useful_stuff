# useful_stuff
Memo for my beloved students

### Keyboard's shortcuts (Mac)
#### Special characters
```ruby
{ # alt + (
} # alt + )
[ # alt + shift + (
] # alt + shift + )
| # alt + shift + l
~ # alt + n
\ # alt + /
```

#### Navigate
```ruby
from one program to another                # cmd + tab
from one window to another (same program)  # cmd + `
```

#### Sublime Text
```ruby
open a file in current project             # cmd + p (or cmd + t)
move a line upwards in file                # ctrl + cmd + ↑
move a line downwards in file              # ctrl + cmd + ↓
(un)comment lines                          # cmd + /
search in file                             # cmd + f
search in project                          # cmd + shift + f
add package                                # cmd + shift + p
add indentation                            # tab
remove indentation                         # shift + tab
move text cursor to next word              # alt + →
move text cursor to previous word          # alt + ←
move text cursor to end of line            # cmd + →
move text cursor to beginning of line      # cmd + ←
close tab                                  # cmd + w
reopen last tab closed                     # cmd + shift + t
navigate to tab on the right               # cmd + alt + →
navigate to tab on the left                # cmd + alt + ←
```

#### Terminal
```ruby
open a new tab                             # cmd + t
close tab                                  # cmd + w
clear window (keeping history)             # ctrl + l
clear window (losing history)              # cmd + k
reach beginning of line                    # ctrl + a
reach end of line                          # ctrl + e
erase the whole line                       # ctrl + u
```

#### Chrome
```ruby
open developer tools (elements)            # cmd + alt + i
open developer tools (console)             # cmd + alt + j
change docking location                    # cmd + shift + d

navigate to tab on the right               # cmd + alt + →
navigate to tab on the left                # cmd + alt + ←
open a new tab                             # cmd + t
focus on address bar                       # cmd + l
close tab                                  # cmd + w
reopen last tab closed                     # cmd + shift + t
```

### Keyboard's shortcuts (LINUX)

#### Sublime Text
```ruby
open a file in current project             # ctrl + p
move a line upwards in file                # ctrl + shift + ↑
move a line downwards in file              # ctrl + shift + ↓
(un)comment lines                          # ctrl + shift + :
search in file                             # ctrl + f
search in project                          # ctrl + shift + f
add package                                # ctrl + shift + p
add indentation                            # tab
remove indentation                         # shift + tab
move text cursor to next word              # alt + →
move text cursor to previous word          # alt + ←
close tab                                  # ctrl + w
reopen last tab closed                     # ctrl + shift + t
```

#### Terminal
```ruby
open a new tab                             # ctrl + shift + t
close tab                                  # ctrl + shift + w
clear window                               # ctrl + L (or type "clear" in terminal)
```

### Conflicts solving
When you can't merge a PR due to conflicts in an `unmergeable_branch`, follow this process:

```ruby
# go to your local master branch
git checkout master

# update your master branch locally with github's master
git pull origin master

# go back to unmergeable_branch
git checkout unmergeable_branch

# merger master in unmergeable branch to solve conflicts locally
git merge master

# now you've fetched all conflicts locally, time to solve them
# open sublime and solve conflicts (locate them with cmd + shift + f <<<<<<<)

# commit your code
git add .
git commit -m "conflict solving"
git push origin unmergeable_branch

# open your PR on github to merge it
hub browse

# merge your PR on github

# go back to your terminal and update your local master with merged files
git checkout master
git pull origin master

# create a new branch for next feature
git checkout -b next_feature
```

### Frequent error messages

##### ``NoMethodError: undefined method `some_method' for nil:NilClass``
It doesn't mean that `some_method` is undefined, it means that `some_object` **on which you call** `.some_method` is nil:
```ruby
recipe.name
# => NoMethodError: undefined method `name' for nil:NilClass
# `recipe` is nil, it shouldn't, fix it
```

##### `PG::ConnectionBad - could not connect to server: No such file or directory Is the server running locally and accepting connections on Unix domain socket "/tmp/.s.PGSQL.5432"?`
It means that PG did not exit gracefully last time your computer was shut off.
Run the following in your terminal:
```bash
rm /usr/local/var/postgres/postmaster.pid
```
