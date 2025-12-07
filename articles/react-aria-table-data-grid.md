---
title: "React AriaのTableの挙動をData Gridパターンから理解する"
emoji: "🎄"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["react", "reactaria", "a11y"]
published: false
---

この記事は、カオナビ Advent Calendar 2025（シリーズ1）11日目です。

https://qiita.com/advent-calendar/2025/kaonavi

## はじめに

[React Aria](https://react-spectrum.adobe.com/react-aria/)には、アクセシビリティに配慮した多くのコンポーネントが用意されていて、その1つに[`Table`](https://react-spectrum.adobe.com/react-aria/Table.html)コンポーネントがあります。

https://react-spectrum.adobe.com/react-aria/Table.html

`Table`コンポーネントによって高機能な表形式のUIを実現できますが、HTMLが持つ[`<table>`要素](https://developer.mozilla.org/ja/docs/Web/HTML/Reference/Elements/table) や一般的なウェブアプリケーションの表形式UI[^1]とは異なる振る舞いがあり、基準となるメンタルモデルを持てないとその挙動に戸惑うことがあります。一見似た構造ですが、`<table>` の延長線上にあるUIではありません。
特に、tab や矢印キーによるフォーカス移動など、一般的な `<table>` の操作感とは異なるキーボード挙動が戸惑いの原因になりやすいポイントだと思います。
この記事では、React Ariaの`Table`コンポーネントがどのように振る舞うのか、ベースとなっている考え方を学び、その理解の取っ掛かりとなることに焦点をあてます。

:::message
この記事は、React Ariaの`Table` [v3.17.8](https://react-spectrum.adobe.com/releases/2025-10-02.html) 時点の情報をもとに記載しています。
:::

[^1]: 主観的な観測に基づくものですが、一般的なウェブアプリケーションの表形式UIとは、例えばGoogleスプレッドシート、あるいはNotionのカレンダーやGitHubのプロジェクトなどのUIを指します。

## ベースにあるData Gridパターン

React Ariaの`Table`コンポーネントは、ベースにARIA gridパターンを採用していることが公式ドキュメントへ記載されている以下の1文に示されています。

> **Accessible** – Follows the [ARIA grid pattern](https://www.w3.org/WAI/ARIA/apg/patterns/grid/), with additional selection announcements via an ARIA live region. Extensively tested across many devices and assistive technologies to ensure announcements and behaviors are consistent.
>
> https://react-spectrum.adobe.com/react-aria/Table.html#features

ARIA gridパターンとは、[WAI-ARIA Authoring Practices Guide（APG）](https://www.w3.org/WAI/ARIA/apg/) [^2]に記載されている、アクセシブルな表形式のUIを構築するための設計パターンです。
React Ariaの`Table`コンポーネントは、このARIA gridパターンをベースにしているため、一般的な表形式のUIとは異なる振る舞いをします。

[^2]: ARIA Authoring Practices Guideは、WAI-ARIAを活用してアクセシブルなUIを実装するためのガイドとなるW3Cのドキュメントです。 https://www.w3.org/WAI/ARIA/apg/

関係性を整理すると以下の図のようになるでしょう。

![React Aria TableとARIAパターンとの関係図](https://storage.googleapis.com/zenn-user-upload/9250889a65c6-20251129.png)

ひとことに「表」といっても、WAI-ARIAの`role`[^3]としては、`table`と`grid`という2つの概念があります。

| role | 概要 |
| ---- | ---- |
| `table` | HTMLの`<table>`要素に相当する。静的な表形式データのUIに使用する。 |
| `grid` | インタラクティブな表形式UIに対応する役割。セルの選択や編集、ソートなどの操作が可能なUIに使用する。 |

[^3]: roleとは、ユーザーインターフェースの要素種別を示す属性です。 https://developer.mozilla.org/ja/docs/Web/Accessibility/ARIA

静的な表形式のデータ表示には`table`ですが、インタラクションが伴う表形式UIには`grid`という分類です。「テーブル」というワードが一般的に使われることが多いため、混同することも多いのではと思いますが、ARIAの観点ではこのように区別されています。

そして、[ARIA grid pattern](https://www.w3.org/WAI/ARIA/apg/patterns/grid/)では、`grid`のパターンを2つのカテゴリーに分けています。

> Uses of the grid pattern broadly fall into two categories: presenting tabular information (data grids) and grouping other widgets (layout grids). 
> 
> https://www.w3.org/WAI/ARIA/apg/patterns/grid/

| カテゴリー | 概要 |
| ---------- | ---- |
| Data Grids | 表形式の情報を提示するために使用されるグリッド。セルの選択や編集、ソートなどの操作が可能なUIに使用する。 |
| Layout Grids | 他のウィジェットをグループ化するために使用されるグリッド。レイアウト目的で使用され、セルの選択や編集などの操作は通常含まれない。 |

React Ariaの`Table`は、データ表示に対するコンポーネントなので、ARIA gridパターンの中でも「Data Grids」に該当すると言えるでしょう。
したがって、React Ariaの`Table`コンポーネントを理解するためには、このData Gridパターンについて知ることが必要になります。

## Data Gridパターン

では、Data Gridパターンとは具体的にどのようなものなのでしょうか。ツリー構造で見ると以下のようになります。

![Data Gridパターンのツリー構造](https://storage.googleapis.com/zenn-user-upload/84f2c441ea09-20251203.png)

[`table`要素の構造](https://www.w3.org/WAI/ARIA/apg/patterns/table/)とおおむね同じような構造になっていますが、

- `gridcell`、`columnheader`、`rowheader`といったセル（またはその内部の要素）にはフォーカス可能で、特に`gridcell`はフォーカス必須
- `columnheader`や`rowheader`も基本的にフォーカス可能であるものの、操作可能ではないセルであれば例外的にフォーカス必須ではない
  - フォーカス可能ではないというのは、例えばソートやフィルターといった操作機能を持たないヘッダーセルのような場合

といったあたりの特徴に違いがみられます。
基本的に全てのセルがフォーカス可能であることで、キーボード操作でセル間を移動したり、セルの内容を編集したりといった操作が可能なものへとつながります。

### キーボード操作

`grid`へのフォーカスは、`tab`キーで可能ですが、`tab`キーでセル間を移動することはできません。`tab`キーでフォーカスし、フォーカスしている状態で`tab`キーを押すとフォーカスが外れます。

![tabキーでフォーカスする](https://storage.googleapis.com/zenn-user-upload/ac71dc6777af-20251203.png =400x)
![tabキーでフォーカスを外す](https://storage.googleapis.com/zenn-user-upload/8abfd4243910-20251203.png =400x)

`tab`キーによる移動は`grid`全体へのフォーカスの付与と解除という形であり、`grid`の中のセル間の移動は矢印キー等で行う、というのがData Gridパターンのキーボード操作となります。
おそらく`tab`キーによる移動を想定していると、ここで戸惑うことになるでしょう。

![セル間移動は矢印キーで可能](https://storage.googleapis.com/zenn-user-upload/201862681889-20251203.png =320x)

tab キーは “グリッドというウィジェット全体の出入り” に使い、  セル間の移動は矢印キーに統一する、というのが Grid パターンの基本的な思想だと理解すると良いかもしれません。

一方、セル間移動の挙動は以下のように「右端まで右矢印キーで移動したらフォーカスはそれ以上移動しない」とありますが、

> Right Arrow: Moves focus one cell to the right. If focus is on the right-most cell in the row, focus does not move.
> 
> https://www.w3.org/WAI/ARIA/apg/patterns/grid/#datagridsforpresentingtabularinformation

この点はReact Ariaの`Table`コンポーネントでは異なり、右端まで移動した後に右矢印キーを押すと同一行の左端へフォーカスが移動するように[公式ドキュメントのサンプル](https://react-spectrum.adobe.com/react-aria/Table.html#example)では動きます。
このような差異を踏まえると、React Ariaの`Table`は「Data Gridパターンのコアとなる構造やフォーカスモデルには従っている。ただし、その全ての記述に従っているわけでない」と言えそうです。

なお、ARIA Authoring Practices Guide には[より高度なセル内部のフォーカス制御](https://www.w3.org/WAI/ARIA/apg/patterns/grid/#keyboardinteraction-settingfocusandnavigatinginsidecells)も定義されていますが、React Ariaの `Table` の基本的な振る舞いの理解の範疇からは離れるので割愛します。

## Data Gridパターンをふまえて見るReact Ariaの`Table`コンポーネント

ここまで見てきたように、名前こそ “Table” ですが、実態としては ARIA Grid パターンに基づく“インタラクティブな表形式のUI” の性質を持っています。
そのため、HTML table や一般的なTableライブラリーと比べると、挙動に戸惑いを感じる場合があると思います。

React Aria の `Table` を理解するうえで重要なのは、これが “HTML table のアクセシブル版” ではなく、“Data Grid の考え方を土台にしたインタラクティブな表形式 UI” であるという点です。

この視点を持つことで、セルのフォーカスや tab と矢印キーの扱いの違いといったポイントが腑に落ちやすくなると思います。
また、Data Gridパターンを理解することで、React Ariaの`Table`コンポーネントの挙動を予測しやすくなると考えられます。

## 参考

- [Table – React Aria](https://react-spectrum.adobe.com/react-aria/Table.html)
- [Grid (Interactive Tabular Data and Layout Containers) Pattern | APG | WAI | W3C](https://www.w3.org/WAI/ARIA/apg/patterns/grid/)
- [Table Pattern | APG | WAI | W3C](https://www.w3.org/WAI/ARIA/apg/patterns/table/)
- [`<table>`: 表要素 - HTML | MDN](https://developer.mozilla.org/ja/docs/Web/HTML/Reference/Elements/table)