ElasticSearch SQL Client
=======

![GitHub branch check runs](https://img.shields.io/github/check-runs/datamin-io/es-sql-client/main?color=green)
![GitHub go.mod Go version](https://img.shields.io/github/go-mod/go-version/datamin-io/es-sql-client?color=blue)
<a href="https://github.com/datamin-io/es-sql-client?tab=Apache-2.0-1-ov-file">![Static Badge](https://img.shields.io/badge/license-Apache%202.0-blue)</a>
<a href="https://datamin.io" target="_blank">![Static Badge](https://img.shields.io/badge/website-datamin.io-blue)</a>
<a href="https://docs.datamin.io" target="_blank">![Static Badge](https://img.shields.io/badge/documentation-docs.datamin.io-blue)</a>
<a href="https://join.slack.com/t/datamincommunity/shared_invite/zt-2nawzl6h0-qqJ0j7Vx_AEHfnB45xJg2Q" target="_blank">![Static Badge](https://img.shields.io/badge/community-join%20Slack-blue)</a>

Example usage

```go
logger := log.StandardLogger()
lvl, _ := log.ParseLevel("trace")
logger.SetLevel(lvl)

client := CreateWithBaseUrl(
    context.Background(),
    "http://localhost:9200",
    nil,
)

_, err := client.Version(nil)
if err != nil {
    panic(err)
}

client.SetLogger(logger)

result, err := client.SqlQuery(`SELECT * FROM kibana_sample_data_ecommerce WHERE "category" = 'Men''s Shoes' LIMIT 2`)
if err != nil {
    panic(err)
}

b, err := json.Marshal(result.Rows)

fmt.Printf("result: %s\n", string(b))
```
