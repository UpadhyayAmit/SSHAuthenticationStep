# Authenticate with SSH in git

## Checking for existing SSH keys

1.	Open Git Bash.
2.	Enter ls -al ~/.ssh to see if existing SSH keys are present:
3.	$ ls -al ~/.ssh
## Lists the files in your .ssh directory, if they exist
4.	Check the directory listing to see if you already have a public SSH key. By default, the filenames of the public keys are one of the following:
-	id_rsa.pub
-	id_ecdsa.pub
-	id_ed25519.pub

If you don't have an existing public and private key pair, or don't wish to use any that are available to connect to GitHub, then generate a new SSH key.

If you see an existing public and private key pair listed (for example id_rsa.pub and id_rsa) that you would like to use to connect to GitHub, you can add your SSH key to the ssh-agent.


## Generating a new SSH key
1.	Open Git Bash.
2.	Paste the text below, substituting in your GitHub email address.

$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

This creates a new ssh key, using the provided email as a label.
- Generating public/private rsa key pair.

3.	When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.
- Enter a file in which to save the key (/c/Users/you/.ssh/id_rsa):[Press enter]

4.	At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases".

5.	- Enter passphrase (empty for no passphrase): [Type a passphrase]

- Enter same passphrase again: [Type passphrase again]


## Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key.

If you have GitHub Desktop installed, you can use it to clone repositories and not deal with SSH keys. It also comes with the Git Bash tool, which is the preferred way of running git commands on Windows.

1.	Ensure the ssh-agent is running:
-	If you are using the Git Shell that's installed with GitHub Desktop, the ssh-agent should be running.
-	If you are using another terminal prompt, such as Git for Windows, you can use the "Auto-launching the ssh-agent" instructions in "Working with SSH key passphrases", or start it manually:
-	## start the ssh-agent in the background
-	$ eval $(ssh-agent -s)
- Agent pid 59566

2.	Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

$ ssh-add ~/.ssh/id_rsa


#Copy the SSH key to your clipboard.

If your SSH key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

# Adding a new SSH key to your GitHub account
$ clip < ~/.ssh/id_rsa.pub

# Copies the contents of the id_rsa.pub file to your clipboard
- Click New SSH key or Add SSH key.


