---
sourcePath: en/ydb/ydb-docs-core/en/core/reference/ydb-sdk/recipes/auth/_includes/env.md
---
# Authentication using environment variables

{% include [work in progress message](../../_includes/addition.md) %}

When using this method, the authentication mode and its parameters are defined by the environment that an application is run in, [as described here](../../../auth.md#env).

By setting one of the following environment variables, you can control the authentication method:

* `YDB_SERVICE_ACCOUNT_KEY_FILE_CREDENTIALS=<path/to/sa_key_file>`: Use a service account file in Yandex.Cloud.
* `YDB_ANONYMOUS_CREDENTIALS="1"`: Use anonymous authentication. Relevant for testing against a Docker container with {{ ydb-short-name }}.
* `YDB_METADATA_CREDENTIALS="1"`: Use the metadata service inside Yandex.Cloud (a Yandex function or a VM).
* `YDB_ACCESS_TOKEN_CREDENTIALS=<access_token>`: Use token-based authentication.

Below are examples of the code for authentication using environment variables in different {{ ydb-short-name }} SDKs.

{% list tabs %}

- Go

  {% include [go.md](env/go.md) %}

{% endlist %}

