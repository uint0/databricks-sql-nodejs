# Release History

## 0.1.x (Unreleased)

- `DBSQLOperation` interface simplified: `HiveUtils` were removed and replaced with new methods
  `DBSQLOperation.fetchChunk`/`DBSQLOperation.fetchAll`. New API implements all necessary waiting
  and data conversion routines internally
- Better TypeScript support
- Thrift definitions updated to support additional Databricks features
- User-agent string updated; a part of user-agent string is configurable through `DBSQLClient`'s `clientId` option
- Connection now uses keep-alive (not configurable at this moment)
- `DBSQLClient` now prepends slash to path when needed
- `DBSQLOperation`: default chunk size for data fetching increased from 100 to 100.000

### Upgrading

`DBSQLClient.utils` was permanently removed. Code which used `utils.waitUntilReady`, `utils.fetchAll`
and `utils.getResult` to get data should now be replaced with the single `DBSQLOperation.fetchAll` method.
Progress reporting, previously supported by `utils.waitUntilReady`, is now configurable via
`DBSQLOperation.fetchChunk`/`DBSQLOperation.fetchAll` options. `DBSQLOperation.setMaxRows` also became
an option of methods mentioned above.

## 0.1.8-beta.1 (2022-06-24)

- Initial release
