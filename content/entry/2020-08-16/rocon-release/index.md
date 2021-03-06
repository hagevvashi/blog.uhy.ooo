---
title: 究極のReact向けルーターライブラリ「Rocon」正式リリース
published: "2020-08-16T23:00+09:00"
tags:
  - Rocon
  - React
  - TypeScript
---

こんにちは。[前回の記事](/entry/2020-08-10/rocon-alpha/)でご説明したReact向けのルーターライブラリ「**Rocon**」をこの度正式リリース（`1.0.0`リリース）したのでご報告します。

Roconに関する詳しいことは前回の記事をご覧いただきたいのですが、簡単に説明するとRoconの特徴は**非常に型安全**であることです。
API面での特徴は、`/:id/profile`のように文字列を用いてルートを定義するのをやめて、代わりにルートを全てオブジェクトとして定義することです。
例えば、`/:id/profile`に相当するルート（`:id`の部分は任意の文字列を入れてアクセス可能という意味になります）はRoconでは次のように定義します。

```tsx
const topLevel = Rocon.Path()
  .any("id");

const secondLevel = topLevel.anyRoute
  .attach(Rocon.Path())
  .route("profile", (r) => r.action(({ id }) => <p>
    Welcome, user {id}!
  </p>));
```

このようにすることで、このルートには任意に決められる部分があり、それに`id`という名前をつけたことが型システム上明らかになります。
これにより、より型安全な取り扱いが可能となるのです。

このアイデアをベースとして、ルーターライブラリに必要な一通りの機能を揃えてできたのがRoconです。
ひとまず最低限ルーターライブラリに必要な機能を取り揃えたので正式リリースとしましたが、今後もユースケースに応じて機能を拡張していくつもりです。

皆さんも機会があればぜひ使っていただけると幸いです。

- チュートリアル・ドキュメント: https://rocon.uhyohyo.net/
- GitHub: https://github.com/uhyo/rocon （スターをお待ちしています🥺）