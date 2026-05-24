# NEON DROP ULTRA Firebase完全接続版

かいと用のFirebase設定を入れた完全接続版です。

## できること

- Firebase Authentication
- ゲストログイン
- Googleログイン
- Firestoreオンラインランキング取得
- Firestoreスコア送信
- ゲーム本体
- ガチャ
- 育成
- 広告報酬デモ

## まず確認

`www/index.html` をブラウザで開いて確認できます。

## Firestoreルール

Firebase Console の Firestore Database > ルール にこれを入れてください。

```js
rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {
    match /rankings/{docId} {
      allow read: if true;
      allow create: if request.auth != null;
      allow update, delete: if false;
    }
  }
}
```

## PCでアプリ化

```bash
npm install
npx cap add ios
npx cap add android
npx cap sync
```
