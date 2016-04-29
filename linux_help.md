### Linux Help 

#### General Help

As with "all" Linux related questions, get help from the help option (-h --h -help --help) or the manual: 
```Linux
<command> --help
man <command>
## there is even a manual for the manual
man man
# scroll down with <enter> or leave with <q> 
```

#### Permissions and chmod

It is important to set the permissions for group folders and subfolder. Here a short overview and below some more details. 

If you create a new folder only you will be able to write (change) anything in the folder or the folder itself. Only the owner (and of course the admin) can change permissions by default.

```Linux
mkdir -p /scicore/home/holmp/GROUP/test/test2/
# d **rwx** r-x r-x  2 walser   holmp   512 Apr 29 10:50 test/
chmod 776 /scicore/home/holmp/GROUP/test
# d **rwx rwx rw-**  2 walser   holmp   512 Apr 29 10:50 test/
# d **rwx** r-x r-x  2 walser   holmp   512 Apr 29 10:50 test/test2/
chmod -R 776 /scicore/home/holmp/GROUP/test ## change files and directories
# d **rwx rwx rw-**  2 walser   holmp   512 Apr 29 10:50 test/
# d **rwx rwx rw-**  2 walser   holmp   512 Apr 29 10:50 test/test2
```
There is a short cut ...

```Linux
mkdir -m 776 -p /scicore/home/holmp/GROUP/test
```

##### Understanding Permissions

Each file and directory has permissions (read, write, and execute) for each level (user, group, others). If you do a listing (ls -l) you will see the permissions:

```Example
d | rwx | r-x | r-x > directory|your permissions|group permission|users/all permission
```

The three digits in chmod corresponds to one of the three permission triplets (user, group, others). Every permission bit in a triplet corresponds to a value: 4 for read (r), 2 for write (w), 1 for execute (x), and zero for -.  

| Level         | Permission      | octal |
| ------------- |:---------------:| -----:|
| Triplet for u | rwx > 4 + 2 + 1 |  = 7  |
| Triplet for g | r-x > 4 + 2 + 1 |  = 7  |
| Tripler for o | r-x > 4 + 2 + 0 |  = 6  |
| Compined      |                 |  776  |

