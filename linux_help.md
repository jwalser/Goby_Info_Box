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

```Linux
mkdir /scicore/home/holmp/GROUP/test 
# d **rwx** r-x r-x  2 walser   holmp   512 Apr 29 10:50 test/
chmod 776 /scicore/home/holmp/GROUP/test
# d **rwx rwx rw-**  2 walser   holmp   512 Apr 29 10:50 test/
```


d|rwx|r-x|r-x > directory|your permissions|group permission|users permission

(r) read<br>
(w) write<br>
(x) execute<br>

| Level         | Permission      | octal |
| ------------- |:---------------:| -----:|
| Triplet for u | rwx > 4 + 2 + 1 |  = 7  |
| Triplet for g | r-x > 4 + 0 + 1 |  = 5  |
| Tripler for o | r-x > 4 + 0 + 1 |  = 5  |
| Compined      |                 |  755  |


If you create a new folder only you will be able to write (change) anything in the folder or the folder itself. Only the owner (and of course the admin) can change permissions by default.

```Linux
mkdir /scicore/home/holmp/GROUP/test 
# d **rwx** r-x r-x  2 walser   holmp   512 Apr 29 10:50 test/
chmod 776 /scicore/home/holmp/GROUP/test
# d **rwx rwx rw-**  2 walser   holmp   512 Apr 29 10:50 test/
```
