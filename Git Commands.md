1. Git global auth/credentials
```
git config --global user.email "villanuevajoshua27@gmail.com"
git config --global user.name "koykoy027"
```
---

2. Git remote auth/credentials
```
git config user.email "villanuevajoshua27@gmail.com"
git config user.name "koykoy027"
```
---

3. How to Login via Personal access token
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

---

4. How to upload project into new repository
```
git init
```
```
git add .
```
```
git commit -m "inital commit"
```

---


```
git remote add origin <repo link>
```
```
git push -u origin master
```
