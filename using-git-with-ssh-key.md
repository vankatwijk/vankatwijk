# using git with ssh key

### most common problem is when you have multiple keys and git does not know which to use then you can force it
forcing git to use a specific ssh key
```
git clone git@gitlab.svcs.int.<site-domain>.com:crm/v1.git --config core.sshCommand="ssh -i ~/certificates/site-domain"
```

# check these sites for reference
```
https://stackoverflow.com/questions/41714882/git-how-to-clone-with-ssh-key-username
https://www.toolsqa.com/git/clone-repository-using-ssh/
```

# if the above sites done exist here is the relivant informaiton

### Step 1: Check for existing SSH keys
```
$> ls -al ~/.ssh

Do you see any files named id_rsa and id_rsa.pub?

If yes go to Step 3

If no, you need to generate them
```
### Step 2: Generate a new SSH key
```
$> ssh-keygen -t rsa -b 4096 -C "yourEmail"

Add your SSH key to the ssh-agent

$> eval "$(ssh-agent -s)"

$> ssh-add ~/.ssh/id_rsa
```
### Step 3.1: Add the SSH key to your GIT account.
```
Get your public key

$> cat ~/.ssh/id_rsa.pub

Go to your GIT project -> Settings -> SSH keys

Then past the content of your public key in SSH keys
```
### Step 3.2: Force SSH Client To Use Given Private Key
```
This is an alternative solution when you can't set keys on your Git account

$> sudo nano ~/.ssh/config

Then change this line

IdentityFile <yourPrivateKey>
```
### Step 4: Clone the project
```
$> git clone git@xxxxx.com:xxx/xxx/git
```
