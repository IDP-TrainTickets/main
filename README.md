# Testing

## Starting up the services

```bash
docker swarm init
docker stack deploy -c stack.yml app_stack
```

## Using the services

1. Creating a user

```bash
curl -i http://localhost:8022/auth/register -H "Content-Type: application/json" -d '{"username":"admin","password":"password123"}'
```

2. Loging in / getting a JWT token

```bash
curl -i http://localhost:8022/auth/login -H "Content-Type: application/json" -d '{"username":"admin","password":"password123"}'
```

3. Checking JWT validation with Kong

```bash
curl -i http://localhost:8022/api/test -H "Authorization: Bearer <token>"   -H "Content-Type: application/json"   -d '{"username":"admin","password":"password123"}'
```
