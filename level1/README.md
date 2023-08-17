# S3でindex.htmlを公開する。
> [参考](https://zenn.dev/longbridge/articles/30da1524649ef9)
> [OAC対応バージョン](https://dev.classmethod.jp/articles/amazon-cloudfront-origin-access-control/)

## S3の設定
### バケットの作成
- パブリックアクセスを許可

### バケットの設定
- Properties --> Static website hostingを有効に
- インデックスドキュメントとエラードキュメントにindex.htmlを指定
- Permissions --> Bucket Policyに以下を設定

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::バケット名/*"
            ]
        }
    ]
}
```

### デプロイする
- index.htmlを作成してアップロードする。
- Properties --> Static website hostingから見られるURLにアクセスする。
