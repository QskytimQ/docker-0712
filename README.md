# Docker 7/12 

## Docker image 練習
### 登入Harbor
```
docker login 140.92.90.60:32443
```
`帳號:user 密碼:User000!`

### Pull image
```
docker pull 140.92.90.60:32443/dockerhub/library/nginx:1.19
```

### 修改image tag
```
docker tag 140.92.90.60:32443/dockerhub/library/nginx:1.19 140.92.90.60:32443/user/nginx:{IP第四碼}-{帳號末三碼}
```

### Push image 至Harbor
```
docker push 140.92.90.60:32443/user/nginx:{IP第四碼}-{帳號末三碼}
```
---

## Docker process 練習

### 建立container
```
docker run -itd -p 8081:80 -v $PWD/html:/usr/share/nginx/html/ --name nginx-001 localhost:32443/dockerhub/library/nginx:1.19
```
`ex: user001 port:8081, name:nginx-001`

### 驗證
```
http://{VM 外部IP}:8081/
```

### 修改 html/index.html
```
vim html/index.html 
```

### 停止及刪除container
```
docker stop nginx-001
docker rm nginx-001
```
---
## Dockerflie 建立
### 範例一 Flask
#### 在docker file 這層，執行build
```
cd dockerfile/flask
docker build . --tag flask:001
```
#### 運行
```
docker run -itd -p 5001:5000 --name flask-001 flask:001
```
#### 檢查狀態
```
docker ps –a | grep flask
```
---
### 範例二 VueJS
#### 建置image
```
cd dockerfile/vuejs
docker build . --tag vuejs:001
```
#### 運行
```
docker run -itd -p 3001:80 --name vuejs-001 vuejs:001
```
#### 檢查狀態
```
docker ps –a | grep vuejs
```

---
### 範例三 ASP.NET 
#### 建置image
```
cd dockerfile/asp-dotnet-core
docker build . --tag asp:001
```
#### 運行
```
docker run -itd -p 8001:80 --name asp-001 asp:001
```
#### 檢查狀態
```
docker ps -a | grep asp
```
