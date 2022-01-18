# learn-app-runner

## build

```
docker build -t 609014044253.dkr.ecr.ap-northeast-1.amazonaws.com/hello-express . 
docker tag hello-express:latest 609014044253.dkr.ecr.ap-northeast-1.amazonaws.com/hello-express:latest
```

## deploy

```
aws configure --profile kazuhisa_fukuda@admin
export AWS_DEFAULT_PROFILE=kazuhisa_fukuda@admin
aws ecr get-login-password --profile kazuhisa_fukuda@admin | docker login --username AWS --password-stdin 609014044253.dkr.ecr.ap-northeast-1.amazonaws.com/hello-express
docker push 609014044253.dkr.ecr.ap-northeast-1.amazonaws.com/hello-express:latest
```

Then, set service manually.(Don't worry. It's so easy!)
https://ap-northeast-1.console.aws.amazon.com/apprunner/home?region=ap-northeast-1#/services

## Note
Need to set architecture to `x86_64`.

```Dockerfile
FROM --platform=linux/amd64 node:14
```

## Reference
https://qiita.com/Kouichi_Itagaki/items/4aa174a2993e8cc87ebe