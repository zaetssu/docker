### 4 балла

```
Логи:
2026-11-22 16:09:32,963 listening port=8000 storage=sqlite
2026-11-22 16:16:28,874 http 172.17.0.1 "GET / HTTP/1.1" 200 -
2026-11-22 16:16:28,902 http 172.17.0.1 "POST /increment HTTP/1.1" 200 -
2026-11-22 16:16:28,931 http 172.17.0.1 "POST /increment HTTP/1.1" 200 -

### 6 баллов

{"greeting": "Hello from a compose!", "count": 0, "hostname": "61c09a29e303", "storage": "sqlite"}
{"greeting": "Hello from a compose!", "count": 1, "hostname": "61c09a29e303", "storage": "sqlite"}
{"greeting": "Hello from a compose!", "count": 2, "hostname": "61c09a29e303", "storage": "sqlite"}
{"greeting": "Hello from a compose!", "count": 2, "hostname": "9f2a14c8b110", "storage": "sqlite"}

### 8 баллов

curl -X POST [http://127.0.0.1:8080/increment](http://127.0.0.1:8080/increment)
curl -X POST [http://127.0.0.1:8080/increment](http://127.0.0.1:8080/increment)
docker compose down
docker compose up -d
curl [http://127.0.0.1:8080/](http://127.0.0.1:8080/)
# {"greeting": "Hello from a compose!", "count": 2, "hostname": "04cb5945d31c", "storage": "redis"}

docker compose stop redis
curl [http://127.0.0.1:8080/healthz](http://127.0.0.1:8080/healthz)   
# 200 OK {"status": "alive"}
curl [http://127.0.0.1:8080/readyz](http://127.0.0.1:8080/readyz)   
# 503 Service Unavailable {"error": "storage_unavailable"}
curl -X POST [http://127.0.0.1:8080/increment](http://127.0.0.1:8080/increment)  
# 503 Service Unavailable

docker compose start redis
curl [http://127.0.0.1:8080/](http://127.0.0.1:8080/)
# {"count": 2, "storage": "redis"}
curl -X POST [http://127.0.0.1:8080/increment](http://127.0.0.1:8080/increment)  
# {"count": 3, "storage": "redis"}
```

