#The Premise#
Keeping track of manual changes to a system is difficult, in an ideal world even break fix situations would run through your config management system, but I don't live there.

#Partial Solution#
```bash 
edit /etc/my.cnf
```
Will check /etc/my.cnf into /git repository to track the changes you make to the file. You can select your favourite text editor and there are a selection of aliases you can source into your shell for convience. 

```bash
EDITOR=nano edit /etc/my.cnf
edit -e nano /etc/my.cnf
source /git/aliases
```

###Restores and History###
The file contents and basic metadata about all files is stored in git. This means that you can recover a file from any time in it's history starting with the previous revision or any revision you have the git commit ref for.

```bash 
restore /etc/my.cnf
cd /git
git log --pretty=short -p -n 2 files/etc/my.cnf
/git/restore -r 35c902c3c7 /etc/my.cnf
```

### Ticket References ###
It can be nice to know not only what was changed but also why it was changed.
You can add a ticket id to the git commit log with either the -m switch or by setting the MSG environment variable, perhaps through a script at login

```bash
edit -m 'PB-101' /etc/my.cnf
```
