# ssh key setup for git

---


Using SSH authentication for communicating with remote repos is generally easier than using https. Sometimes it's required for certain repos or by rules set at the hosting level.

Here's how to get set up with SSH keys

1. Create an SSH public/private key pair (skip this if you already have one!)
    1. open git bash (or any other terminal that has git available)
    1. type `ssh-keygen` and press enter
        * press enter to answer each of the following questions with the default answers
    1. as long as you saved your SSH key to the default location, enter the following command: `cat ~/.ssh/id_rsa.pub`
    1. highlight and copy the output (starts with `ssh-rsa` and ends with `username@computer_name`)
    1. navigate to your SSH key settings on your git hosting and add your key to your profile
1. Clone or add the remote to an existing repo per the instructions on the project page using the ssh URL scheme (instead of `https://`)
    * `git clone git@gitawse1.hagerty.com:<username>/<project>`
    * `git remote add origin git@gitawse1.hagerty.com:<username>/<project>`
1. Profit??$?

> You should now be able to use SSH URLs for connections between your terminal and the remote that you copied the key to
