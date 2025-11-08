# Projeto Docker

## - Para subir o projeto utilize o comando para criar a imagem:

```javascript
docker build -t backend .

```

## - Depois crie uma network com o comando:

```javascript
docker network create mynetwork

```

## - Utilize o comando abaixo para subir o Postgres:

```javascript
docker run -d \
 --name mypostgres \
 --network mynetwork \
 -p 5433:5432 \
 -e POSTGRES_PASSWORD=postgres \
postgres

```

## - E por fim, construa o container com o comando:

```javascript
docker run -d \
	--name backend \
	--network mynetwork \
	-e DATABASE_URL="postgresql://postgres:postgres@mypostgres:5432/mydb?schema=public" \
	-p 5000:5000 \
backend
```

---

## Ou utilize o Docker compose com o comando:

```javascript
docker compose up -d

```
