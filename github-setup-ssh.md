<h1 class="capitalize">Getting Set Up on Github with SSH</h1>

---

<section class="section">
    <h2 class="sentence">Why SSH instead of HTTPS?</h2>

When we use <code>HTTPS</code> when communicating with our **Github** repositories, **Github** will require you to enter your `username`, `email` and `password`.

Credentials are not necessary when using `SSH keys`. `SSH` consists of a `public` and `private key`. The `public key` is ***stored*** on `Github`, and the `private key` is ***stored*** in a safe place on your `computer`.

`SSH keys` are used to recognize your computer/device.

When paired properly, `Github` recognizes that your ***computer*** is the ***only one*** that can push to the repositories associated with your `Github` profile.

***No other*** computer can do that because they **don't contain** either your `public` or `private` key. But the `key` component is the `private key` on your device.

Getting to understand how `SSH Technology` works in the process of setting up a ***profile*** on `Github` makes the **process** of ***pushing projects*** to `Github` easier.

</section>

---

<section class="section">
    <h2 class="sentence">What is SSH?</h2>

`SSH` stands for `Secure Shell`, and it is a ***method*** for `secure remote login` from ***one computer*** to ***another***.</li>

</section>

---

<section class="section">
    <h2 class="sentence">Why Use SSH?</h2>

`SSH` provides several alternative ***options*** for `strong authentication`, and it ***protects*** the communication's `security` and `integrity` with `strong encryption`.

`SSH` is a ***secure alternative*** to the **non-protected** `login protocals` such as <a href="https://www.ssh.com/ssh/telnet">telnet</a> or <a href="https://www.ssh.com/ssh/rlogin">rlogin</a> and ***insecure*** `file transfer methods` such as <a href="https://www.ssh.com/ssh/ftp/">FTP</a>.

</section>

---

<section class="section">
    <h2 class="sentence">Authentication with SSH</h2>

`Authentication` works through the ***exchange*** of `public` and `private` ***keys***. These `keys` are stored in files.

A `public key` is ***stored*** on a `trusted server` such as `Github`, and a `private key` is ***stored*** on `your device`.

</section>

---

<section class="section">
    <h2 class="sentence">Using SSH</h2>

In order be able to use `SSH`, you have to ***generate*** a `public` and `private` ***key pair***.

The ***pair*** is usually stored in an `~/.ssh` directory which ***only exists*** if you **already** have ***created*** `SSH` keys in the past.

***Before creating*** your `key pair`, first ***check*** if you **already have** a `key pair` by cding into `~/.ssh`. If you do have a key pair, ***skip*** to the `last step`.

```shell
cd ~/.ssh
ls 
# if you get anything back that ends in `.pub`, 
# you might have SSH keys!
```
</section>

---

<section class="section">
    <h2 class="sentence">Creating Your Keys</h2>

Use the following commands to generate a new key pair:

```shell
ssh-keygen -t rsa -C "youremail@example.com"
# Enter the file in which to save the key pair(/Users/username/.ssh/id_rsa): [Press Enter]
# Enter passphrase (empty for no passphrase): [Type a passphrase]
# Enter the same passphrase again: [Type passphrase]
```

If ***everything*** goes **well**, you'll ***receive*** a `message` stating that your `keys` have been ***saved***.

</section>

---

<section class="section">
    <h2 class="sentence">Adding Your New Key to ssh-agent</h2>

`ssh-agent` is a ***helper program*** that keeps track of a user's `identity keys` and `passphrases`.

The **agent** can then ***use*** the `keys` to ***log into*** other `servers` ***without*** having the user **type** in a `password` or `passphrase` again. This ***implements*** a form of `single sign-on` (SSO).

</section>

---

<section class="section">
    <h2 class="sentence">Using ssh-agent</h2>

```shell
    # start the ssh-agent in the background
    $ eval "$(ssh-agent -s)"
    # Agent pid 34234<br/>
    # Add your key<br/>
    $ ssh-add ~/.ssh/id_rsa
```

</section>

---

<section class="section">
    <h2 class="sentence">Final Steps: Copying Your Key</h2>

Now that you have ***generated*** and ***stored*** your `SSH` **key pair**, you need to ***copy*** your `public key`. The `instructions` ***assume*** that you have ***named*** your **public key** `id_rsa.pub` (the default name).

Please ***ignore*** the `single quotes`!

```shell
'pbcopy < ~/.ssh/id_rsa.pub'
```
</section>

---

<section class="section">
    <h2 class="sentence">Final Steps: Adding Keys to Your Account(s)</h2>

If you are ***adding*** the **copied** `public key` to `Github`, ***go to*** `Settings -> SSH Keys -> Add SSH Key` on `Github.com`.

***Paste*** what you have **copied** into the `text area`, and ***hit*** the `"Add Key"` **button**.

Now you can ***start using*** the `SSH URL` on `Github` ***instead of*** `HTTPS`.

</section>

---

<section class="section">
    <h2 class="sentence">Related Resources</h2>

-   [SSH Protocol](https://www.ssh.com/ssh/protocol)

-   [ssh-agent - Single Sign-On using SSH](https://www.ssh.com/ssh/agent)

</section>
