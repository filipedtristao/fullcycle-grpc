# Exemplo de implementação de gRPC

1. Suba o container rodando:
```
docker-compose up -d
```

2. Acesse o container:
```
docker-compose exec app sh
```

3. Caso queira gerar novamente as stubs:
```
protoc --proto_path=proto/ proto/*.proto --plugin=$(go env GOPATH)/bin/protoc-gen-go-grpc --go-grpc_out=. --go_out=.
```

4. Iniciar server
```
go run cmd/server/server.go
```

5. Inspecionar o serviço gRPC com evans
```
evans -r repl --host localhost --port 50051
service UserService
call AddUser
```

6. Executando o client com os exemplos
```
go run cmd/client/client.go
```