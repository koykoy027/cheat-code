# Git commands

## Git global auth/credentials
```
git config --global user.email "villanuevajoshua27@gmail.com"
git config --global user.name "koykoy027"
```

## Git remote auth/credentials
```
git config user.email "villanuevajoshua27@gmail.com"
git config user.name "koykoy027"
```

## How to Login via Personal access token
```
git credential-store --file ~/.git-credentials store <<EOF
protocol=https
host=github.com
username=koykoy027
password=`your_personal_access_token`
EOF
```

```
git config --global credential.helper store
```

## Verify Authentication

To check the global Git user name:
```
git config --global user.name

```

To check the global Git user email:
```
git config --global user.email
```

To check the list of all configurations, including user-related configurations:
```
git config --global --list
```

If you are looking to see which user is currently authenticated for a specific repository, you can use the following command:
```
git config user.name
```

If you want to see information about the currently logged-in user on your Ubuntu system, you can use the whoami command:
```
whoami
```

## update git

update default branch, from `master ` to `main`
```
git branch -m master main
git fetch origin
git branch -u main main
git remote set-head origin -a
```

If the remote URL or branch name is incorrect, update it using the following commands
```
git remote set-url origin <new-remote-url>
git branch --set-upstream-to=origin/<correct-branch-name> main
```

## How to ignore all files and folders
```
*
!*gitignore
```
