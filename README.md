## How to connect to GitHub with SSH

There are two ways to connect your local respository to GitHub: HTTPS and SSH.

Below are the steps for SSH.

### 1. Create a .ssh folder

Open up your Git Bash App. Make sure you are in your Home directory. You can check this by typing the following command:

``` cd ~.```

Once in your home directory, check if you already have a .ssh folder, if not create one by using the following command:

```commandline
mkdir .ssh
```

### 2. Create your authentication key

You then need to go into the .ssh folder:

```commandline
cd .ssh
```

Once in the folder, type the following command to create your authentication key.

```
ssh-keygen -t rsa -b 4096 -C "<email address>"

```
Make sure you enter in your own email address. The above command will create public/private rsa key pair. When prompted to enter the file in which to save the key, type the following:

```commandline
<name>-github-key
```
Press enter when prompted to enter in your password. If your keys have been properly created you should see the following image.

![img.png](img.png)

### 3. Associate your SSH keys with GitHub accoun

Head over to github.com and login. Click on your profile, settings and on the lef-hand side click on "SSH and GPG Keys". Then click on "New SSH Keys"
![img_1.png](img_1.png)

You will be prompted to include a title and in box titled "Key" you need to insert your public key. To access your public key, head back to your Git Bash App. Type the following command to access the relevant file:

```commandline
cat <name>-github-key.pub
```
Copy the long public key from the file and paste it in the box on GitHub. Once done, click "Add Key"

### 4. Add agent and authentication

Type the following commands in your Git Bash App:

```commandline
eval ssh-agent -s
ssh-add <name>-github-key
ssh -T git@github.com
```

### Create repository 

When in your Git Bash App, go to the folder where you typically save files for your git repository. Then create a new folder in that folder.

Head over to Git Hub. Click on your profile, then "Repositories" and the click "New".

Give your repository a name and then scroll to the bottom of the page and click "Create Repository". 

Make sure you toggle to "SSH". Git Hub will then provide you will the relevant commands to be entered into your Git Bash App.
```commandline
echo "# test-ssh2" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:<name of  file>.git
git push -u origin main
```

