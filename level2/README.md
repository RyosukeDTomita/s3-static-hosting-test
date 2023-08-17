# CloudFrontでエッジロケーションにキャッシュする
> [参考](https://techblog.nhn-techorus.com/archives/21488)
## 前提条件
- **level1で作成したパケットの静的サイトのホスティング設定は必要ない**
## S3の作成
- Public Accessをすべて許可にする。
- ACLはオフ

## CloudFrontの設定
- ディストリビューションの作成をする。
- Origin domainにs3バケットを選択する。
- Origin Pathは空欄でよい。
- Origin Shieldはオフにする(課金されるため)
> [Origin Shield](https://docs.aws.amazon.com/ja_jp/AmazonCloudFront/latest/DeveloperGuide/origin-shield.html)はオリジンの前にキャッシュレイヤーをおくことでCloud FrontのすべてのキャッシュレイヤーからオリジンへのリクエストがOrigin Shieldを通過するのでキャッシュヒット率が向上し，オリジンへの負荷を下げられる。
- AWS WAFは課金されるのでオンにしない。リクエスト数に対して課金される。

- ディストリビューションが作成されたら，Origins --> Origin domainにあるドメイン/index.htmlでアクセスできる。

### CloudFrontのみからのアクセスをS3バケットに対して許可する。
- Origin Access Controllをディストリビューションで作り，ポリシーをS3に貼り付ける。
> 要らなくなったOACはサイドバーのOrigin Accessから消せる。
