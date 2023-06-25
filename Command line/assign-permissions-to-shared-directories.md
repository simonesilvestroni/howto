# Assign permissions to shared directories

Where `$USER` is the username of the other user, and `$DIR` is the directory (Dropbox or otherwise) you want the other user to have full permissions in:

```bash
sudo chmod -R +a "$USER allow read,write,append,delete,list,search,add_subdirectory,delete_child,file_inherit,directory_inherit" "$DIR"
```

---

#Bash #CommandLine