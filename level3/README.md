# reactアプリをS3に配置してCloudFrontで配信する

## React側の設定

```shell
npx create-react-app hello-react --template typescript # typescript版
cd hello-react
npm run build
```

## S3
- ./build以下をすべてS3にアップロードする。

## CloudFront
- level2の設定を踏襲できる
- Error pagesの設定で403エラー時にindex.htmlを返す設定を追加。
> すぐにはコンテンツの配信が開始されない気がする?うまくいかない時には
- ドメインにアクセスするだけでReactのアプリが配信される。
