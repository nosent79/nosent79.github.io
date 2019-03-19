# Git 계정 여러 개 사용하기


### 새로운 SSH 키 생성하기
```bash
$ cd ~/.ssh
$ ls
id_rsa.pub    id_rsa    known_hosts
```

```bash
$ ssh-keygen -t rsa -C "새 계정의 이메일 주소" 
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/nosent79/.ssh/id_rsa): demo 
// 입력하지 않으면 기존 설정값인 id_rsa 로 지정된다. 
// 본 예제에서는 `demo`로 지정 
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in demo.
Your public key has been saved in demo.pub.
The key fingerprint is:
SHA256:diIjJ2YxtXnwKMZmzOSOP/LsUEYVS6EYirgX6RVeQWs demo@example.com
The key's randomart image is:
+---[RSA 2048]----+
|  . o.@+         |
|o. @ B O         |
|+ + ^ E o        |
| o X = .         |
|. + O + S .      |
| . * + + o       |
|  o o            |
|   = .           |
|   .+            |
+----[SHA256]-----+
$ ls
id_rsa.pub    id_rsa    demo.pub    demo    known_hosts

$ cat demo.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC+PxTg0ZFkw2b/7yH542TrW0yI/CG9/EujaCvorMypWUU3Z1ao7bSNNJ8RNpYXhBUc017r77N2AUHe278ehkPEisGTEfAFu4HCNEEwEcrUOKkyvLnWkA4HPlITCe7l3BtNht99bWklpzFAahfovJ1fCKxu2eRB/80HCabbMT7ww9Q8h54Thv9NwJ4B7UeI6gdl/FBXLJFvgyhQtkXm4Vn9bta85L1OB1FWjuYoaT5biiTNU5VmPEXc2G7JnJAw5gxARZ6Kqv7KPhRsGGoXySpX39BpIUf16R6zDzUbH4IQZSgbEux/NFttLLw36tiklTSiR6q/RPP92gfaEbAIPaPp demo@example.com
```
demo.pub 의 내용을 복사해서 사용한다.

### 등록하기 ###

```bashㅁ
$ ssh-add ~/.ssh/demo
Enter passphrase for /Users/nosent79/.ssh/demo:
Identity added: /Users/nosent79/.ssh/demo (demo@example.com)
```
### config 파일 생성하기 ###
```bash
$ cd ~/.ssh && vi config

# 아래 내용을 입력하자.
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa
  
Host second.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/demo
```

### 추가한 계정으로 푸쉬하기

```bash
$ git init
$ git commit -am "first commit"
$ git remote add origin git@second.github.com:YOURNAME/REPOSITORY.git
$ git push origin master
```

### 새 계정 이름 및 이메일 주소 변경하기
```bash
$ git config user.name "YOURNAME"
$ git config.user.email "YOUREMAIL"
```
<br>
#### 트러블슈팅
`git access denied` 라는 메시지가 나타날 경우 아래 명령어를 실행해준다. 
```bash
$ ssh-add ~/.ssh/demo
```

#### reference
- https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574
