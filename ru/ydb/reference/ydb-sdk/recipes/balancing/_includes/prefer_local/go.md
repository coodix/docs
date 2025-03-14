---
sourcePath: ru/ydb/ydb-docs-core/ru/core/reference/ydb-sdk/recipes/balancing/_includes/prefer_local/go.md
---
```go
package main

import (
	"context"
	"os"

	"github.com/ydb-platform/ydb-go-sdk/v3"
	"github.com/ydb-platform/ydb-go-sdk/v3/balancers"
)

func main() {
	ctx, cancel := context.WithCancel(context.Background())
	defer cancel()
	db, err := ydb.Open(
		ctx,
		os.Getenv("YDB_CONNECTION_STRING"),
		ydb.WithBalancer(
			balancers.PreferLocalDC(
				balancers.RandomChoice(),
			),
		),
	)
	if err != nil {
		panic(err)
	}
	defer func() {
		_ = db.Close(ctx)
	}()
}
```
