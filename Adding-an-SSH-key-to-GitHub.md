You need to do this if you try this command:

```bash
ssh -T git@github.com
```
and you get something that says 

```bash
git@github.com: Permission denied (public key).
```

if you run 

```bash
cat ~/.ssh/id_rsa.pub
```

If you don't see anything, then you can generate a new key with the following command. 
(Skip this step if you saw the key printed to the terminal already)

```bash
ssh-keygen -t rsa -b 4096 -C "your_github@email.com"
```

You'll get a few prompts here, you can confirm the default file location. If you don't
want to have to enter your credentials every time you push to GitHub, you can hit enter
twice more to leave the passphrase blank. Once the key has been generated, you can copy
it to the clipboard with the following command:

```
cat ~/.ssh/id_rsa.pub | pbcopy
```

Note, on Linux, you'll want to use something like `xclip` instead of pbcopy:

```
cat ~/.ssh/id_rsa.pub | xclip -sel clip
```

Or if you'd rather not install anything, you can just open the file and select all and copy:

```
code ~/.ssh/id_rsa.pub
```

Login to GitHub and go to [your ssh key settings](https://github.com/settings/keys)

### Click the Add SSH key button

In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".

### Paste in your SSH key

Your key should be in the clipboard from before. Next you can click the button.

### Click the Add SSH key button

You may be asked to confirm your password at this point.

### Fill in the confirm password form and submit

Finally, to test this out, you can run the following command again to test the SSH connection to GitHub:

```bash
ssh -T git@github.com
```

If all is well, you'll see something like this:

```
Hi DakotaLMartinez! You've successfully authenticated, but GitHub does not provide shell access.
```

And you're good to go! 👍