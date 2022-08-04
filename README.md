# shared terraform action templates

## Set up:

Before committing, please set your git username like this:

```
git config user.name 'tasty sandstone'
git config user.email '110632668+tastysandstone@users.noreply.github.com'
```

_this address found [here in github email settings](https://github.com/settings/emails)_

This way your true identity remains anonymous.

## Why?

The point of this project is to allow for micro-repos containing terraform to use these workflows in their github actions.

This is anonymous so that nobody can see which org you're using it for.

There's a limitation in github where a shared workflow can only be in a public repo.

So, if you use this, and commit to it, do it with a private email such as what's shown above so nobody can glean info on your true Organization or repo.

## How to anonymously push to this repo:

Make a new ssh key just for this repo.

[Go to Github's ssh settings](https://github.com/settings/keys)

Locally, run a command like this:

```
ssh-keygen -t ed25519 -C "some@email.com"

# when it asks you the file name, use something specific for this repo

# then, an easy way to copy the new public key is (on a mac):
cat ~/.ssh/your_key_name.pub | pbcopy
```

Paste that value into the form on Github's ssh key textarea.

Now, locally, give your self an ssh alias for this host:

edit your `~/.ssh/config` file like such:

```
# ----------------------------
# ----------------------------
# github (tastysandstone account)
host github_tastysandstone_account
    User git
    Hostname github.com
    IdentityFile ~/.ssh/id_tastysandstone
# ----------------------------
```

Now, your origin should be like this:

```
git remote add origin git@github_tastysandstone_account:whatever.git
```

where `github_tastysandstone_account` is sort of the magic word that ssh will see and replace with the real host and apply your ssh key.
