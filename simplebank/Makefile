postgres:
	docker run --name postgres16 -p 5433:5432 -e POSTGRES_PASSWORD=SudheerKumar -d postgres
createdb:
	docker exec -it postgres16 createdb --username=postgres --owner=postgres simple_bank

dropdb:
	docker exec -it postgres16 dropdb simple_bank

migrateup:
	migrate -path db/migration -database "postgresql://postgres:SudheerKumar@localhost:5433/simple_bank?sslmode=disable" -verbose up

migratedown:
	migrate -path db/migration -database "postgresql://postgres:SudheerKumar@localhost:5433/simple_bank?sslmode=disable" -verbose down

sqlc:
	sqlc generate

test:
	go test -v -cover ./...

server:
	go run main.go

mock:
	mockgen -package mockdb -destination db/mock/store.go github.com/sudheermurari-07/projects/simplebank/db/sqlc Store

.PHONY: postgres createdb dropdb migarateup migratedown sqlc test server mock