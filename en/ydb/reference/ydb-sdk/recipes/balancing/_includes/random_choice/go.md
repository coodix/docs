---
sourcePath: en/ydb/ydb-docs-core/en/core/reference/ydb-sdk/recipes/balancing/_includes/random_choice/go.md
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
	db, err := ydb.New(
		ctx,
		...
		ydb.WithBalancer(
			balancers.RandomChoice(),
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
