### Permissions and chmod
$

As with "all" Linux related questions, get help from the help option (-h --h -help --help) or the manual: 
```Linux
chmod --help
man chmod
```

d|rwx|r-x|r-x > directory|your permissions|group permission|users permission

(r) read<br>
(w) write<br>
(x) execute<br>

If you create a new folder only you will be able to write (change) anything in the folder or the folder itself. Only the owner (and of course the admin) can change permissions by default.

```Linux
mkdir /scicore/home/holmp/GROUP/test 
d__rwx__r-xr-x  2 walser   holmp   512 Apr 29 10:50 test/
```
