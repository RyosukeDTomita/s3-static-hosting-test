# HTTPSを強制する

## CloudFront
> [UIが変わっていたが一応参考](https://docs.aws.amazon.com/ja_jp/AmazonCloudFront/latest/DeveloperGuide/using-https-viewers-to-cloudfront.html)
- Distributionを選択してBehaviorsから設定できる。
- ViewerをHTTP Onlyにするとhttpでアクセスした時に空白の画面が返される。
- Redirect HTTP to HTTPSにするとhttp通信がhttpsになる。 --> こっちのほうが便利そう。
- ちなみにAmazonが発行した証明書を使っているみたい。


## S3
> [参考](https://dev.classmethod.jp/articles/s3-request-https-only/)
これを見ながらやってみたがhttpのみでしかアクセスできなかった。
ちゃんとやるならドメインと証明書の準備が必要そう。
