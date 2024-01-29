# Домашнее задание к занятию «Запуск приложений в K8S»

<br>

## Задание 1. Создать Deployment и обеспечить доступ к контейнерам приложения по разным портам из другого Pod внутри кластера

1. Манифесты:

[Deployment](./deploymaent.yaml) <br>
[Service](./service_multiport.yaml)

2. Проверка работы service из отдельного pod

```
kubectl exec --stdin --tty multitool -- /bin/bash
multitool:/# curl nginx-mooltitool.default:9001

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```
```
multitool:/# curl nginx-mooltitool.default:9002

WBITT Network MultiTool (with NGINX) - nginx-multitool-7945fdd44-2lb64 - 10.1.211.250 - HTTP: 1180 , HTTPS: 11443 . (Formerly praqma/network-multitool)
```

## Задание 2. Создать Service и обеспечить доступ к приложениям снаружи кластера

1. Манифест:

[Service](./service_nodeport.yaml)

2. Проверка работы NodePort Service

```
curl localhost:30080

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

```
curl localhost:31180

WBITT Network MultiTool (with NGINX) - nginx-multitool-7945fdd44-2lb64 - 10.1.211.250 - HTTP: 1180 , HTTPS: 11443 . (Formerly praqma/network-multitool)
```