---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
title: モブワークを進化させていった話
# some information about the slides, markdown enabled
info: リモートワークになる前からモブワークを実践していって、コロナ禍を経て進化させていった話をしたいと思います。  
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
fonts:
  # basically the text
  sans: 'Noto Sans JP'
  # use with `font-serif` css class from windicss
  serif: 'Noto Serif JP'
  # for code blocks, inline code, etc.
  mono: 'Noto Sans Mono'
addons:
  - "@katzumi/slidev-addon-qrcode"
  - "@katzumi/slidev-addon-blog-card"
  - "slidev-addon-components"
---

# モブワークを進化させていった話

[PHP Conference Japan 2023 懇親会LT](https://phpcon.php.gr.jp/2023/)　Oct 8th, 2023.  
v0.0.2

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/k2tzumi/mob-work-case-study/blob/main/slides.md" target="_blank" alt="GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
layout: two-cols-header
---

# 自己紹介

katzumi（かつみ）と申します。  

「障害のない社会をつくる」をビジョンに掲げている「りたりこ」という会社に所属しています
<a href="https://litalico.co.jp/">
<img src="https://litalico.co.jp/ogp.png" class="w-40" />
</a>

以下のアカウントで活動しています。    

::left::

<img src="https://pbs.twimg.com/profile_images/799890486773170176/KN4gKfS2_400x400.jpg" class="rounded-full w-40 mt-16 mr-12　float-left"/>  
<QRCode width="180" height="180" value="https://twitter.com/katzchum" color="4329B9" image="Logo_of_X.svg" />

<simple-icons-x /> [katzchum](https://twitter.com/katzchum)

::right::

<img src="https://avatars.githubusercontent.com/u/1182787?v=4" class="rounded-full w-40 mt-16 mr-12"/>

<logos-github-octocat /> [k2tzumi](https://github.com/k2tzumi)  
<simple-icons-zenn /> [katzumi](https://zenn.dev/katzumi)  

<br />

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: two-cols-header
transition: fade-out
---


# お願い

写真撮影、SNS での実況について

励みになるので是非ともご意見やご感想など、フィードバック頂けると助かります mm  
あとでスライドを公開します

::left::

<Transform :scale="2.5">
　　　🙆‍♀📷<ph-projector-screen-chart-light /><br />
　　　🙅‍♂📹💸<br />
　　　🙅📸👨‍👦‍👦<br />
</Transform>

::right::

<Transform :scale="2">
<fa6-brands-square-x-twitter />
</Transform>
<br />
<a href="https://twitter.com/search?q=%23phpcon%20%23phpcon2023">#phpcon #phpcon2023</a>

---
layout: fact
---

# What's mob work？

---

# GPT曰く
ペアプロもモブワークの一種

<blockquote>
  <p>モブワークとは、複数人で何かしらの作業（資料作成、プログラミング、事務作業など）を一緒にやっていく作業スタイルのことを指します。</p>
  <p>ペアプログラミングという言葉は聞いたことがあるかもしれませんが、モブプログラミングの一種です。</p>
  <p>ペアプログラミングは2人1組でプログラミングを行うことで、モブプログラミングはそれを2人と決めずに複数人で行うことらしいです。</p>
  <p>このモブプログラミングを、プログラミングに限らず、色々な作業（資料作成、プログラミング、事務作業など）でやってしまうことを モブワーク と呼ぶことがあります。</p>
  <p>この作業スタイルは、テレワークにおいても有効であるとされています</p>
</blockquote>

---

# モブワークのロール
プログラミングの例で説明すると

* Driver  
コードをタイプする人。Navigator の指示どおり動く  
ゴールを目指して手を動かし、実況しながら進めていく

* Navigator  
Driver に指示を出す人。  
先回りして調査をしたりする

---

# ラリーのドライバーとコ・ドライバーとの関連に近い
今だと AI の Copilot に近いかも

<blockquote>
<p>コ・ドライバーとコ・パイロットは、ラリーにおいてドライバーと密接に協力する役割を担う人物です。</p>
<p>コ・ドライバーは、ナビゲーションを担当し、ドライバーに次の方向や曲がり角、障害物などを伝えます。</p>
<p>また、車両の状態を監視し、必要に応じて修理やメンテナンスを行います。</p>
</blockquote>

---
layout: fact
---

# モブワークを実践している人！ 🙋‍♀

---
layout: fact
transition: slide-up
---

# 2020年からモブワークのスタイルで開発を続けています

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/960x1080
---

# モブワークを進化させていったお話

---
transition: fade-out
---

# モブワーク遍歴

- リアル期（2020 年 1 月〜2020 年 3 月）
- フルリモート期（2020 年 4 月〜2021 年 12 月）
- 安定期（2021 年 1 月〜2022 年 3 月）
- プロジェクト立上げ期（2022 年 4 月〜2022 年 6 月）
- チームビルディング期（2022 年 7 月〜2022 年 12 月）
- シン共同開発期（2023 年 1 月〜）

---


# リアル期（2020年1月〜2020年3月）
はいった職場がモブスタイルでした

- 対面にチームメンバーがいる中で zoom を繋げてモブプログラミングを行っていました
- 声は直接届く感じで、相手のデスクトップが画面共有で見る感じ
- モブタイマーはリアルなストップウォッチ
- モブは初めてでしたが、複雑な業務で個人的にはありがたかったです  
技術的な課題もモブで解決するので、立ち上がりが早かったです。

---

# フルリモート期（2020年4月〜2021年12月）
フルリモートになっても仕事のスタイルは変わらず

- 引き続き zoom で繋いでモブプログラミングをしていました  
この当時は時間制限がなくて zoom は神でした
- 音声も zoom 越し経由。カメラ OFF 進行  
すでに見知った顔なのでそんなに不安感なし
- 開発未経験の新人もモブワークに参加した
- モブタイマーを Slack bot 化した  
最初はデスクトップアプリで行っていたけれどタイマーを押せなかったり、気づかなかったり、テンポが良くなかったので改善しました  

---
layout: two-cols-header
---

# モブワークに関するアウトプット

::left::

# 記事にしました

[リモートモブプログラミングを9ヶ月間やってきたので振り返ってみる](https://zenn.dev/katzumi/articles/36bdc74887543c)

<QRCode width="180" height="180" value="https://zenn.dev/katzumi/articles/36bdc74887543c" color="4329B9" image="zenn-dev.svg" />

::right::

# mob-timerを作りました

https://github.com/k2tzumi/mob-timer-bot

<QRCode width="180" height="180" value="https://github.com/k2tzumi/mob-timer-bot" color="4329B9" image="github-mark.svg" />

---


# 安定期（2021年1月〜2022年3月）
暖簾分けしたチームで開発

- メンバーの増減がありつつつも zoom で継続してモブワーク
- バーチャルオフィスを導入して、そこで画面共有する  
zoom の無料期間が終わるなどもあった
- 途中で slack（haddle）に浮気したりしました
- 大きなリリース＆不具合についてもモブでこなす

----

# プロジェクト立上げ期（2022年4月〜2022年6月）
新規プロジェクトを立ち上げを行いました

- はじめはソロで開発をスタート
- 徐々にメンバーが増えていく
- 最初は一人。モブですらない

---

# チームビルディング期（2022年7月〜2022年12月）
チームメンバーが一気に 6 名体制に

- 大分足回りが揃ってきた
- 不安だったメンバーの受け入れを 1 ヶ月程度のモブで立ち上げる手応えがあった
- 複雑な業務知識を独自ドメインで定義して、特化型フレームワークで実装できるようになった
- 具体的な実装イメージは各メンバーの共通認識としてもてるようになった
- ある意味定型業務化したものはソロ活動で実装するようになった
- 複雑なフレームワーク自体もモブで実装するようになった。  
モブタイマーを使って交代制で実装するのではなく、LiveShare や CodeWithMe といった共同プログラミングで行うようになった。  
各メンバーのドメイン知識が溜まり、ドライバーやナビゲーターといった分担ではなく、全員がドライバーで実装するようになった。 
各メンバーの得意不得意があるなかで、ゴリッと実装する人、サポートする人といったメンバーの特性を活かして進められるようになってきた


---

# モブワークの振り返り

- 合う合わないは結構人次第  
疲れるのは確か。過集中になりがちなので、ブレークタイム重要  
→　モブタイマーの活用
- 複雑系の仕組みは多くの目が必要なのでマッチしていた  
そもそも一人で挑むには心が折れる。法律の条文を読み進めるのが難しい。書籍が出ているぐらい 
個人解釈すると危険。業務が回らない自体になりかねない  
- 雑談が重要。ナビゲーションやツッコミがないと、理解が浅いまま進んでしまったり、最大のメリットである多くの目を活かすことができない  
- 20％ルール（非モブ作業で自由に使える時間）があるのも重要  
改善系を意識して行うようになる。非効率な開発すると、人数分のコストがかかる  
- 多様な人が扱うので、わかりやすさ優先な設計になる

---


# 現時点での課題

- まだ知識の偏りはある
- チーム内のコミュニケーションがハイコントラストになりがちで、新しい人が苦労する  
知識量が同じぐらいの人がいないと挫けがち
- メンテナンスし続ける Documents とそうでないものの線引が難しい
- 作るものがある程度見えてない、リードする人がいないと迷走しがちで効率が悪い
- 急に組織はスケールできない。 
徐々にしか人は増やせない。株分けしてチームを増やしていくイメージ

---

# 最後に


- モブワークを実践しているチームの方とお話をしたいです。
- リモートワークを継続して行われている方もお声がけください。
- 複雑な業務を行われている方、どう複雑性と向き合っているか？お話させてください

---
layout: two-cols-header
---

# 宣伝

PHP カンファレンスに登壇しました！

全国制覇目指す？ｗ

::left::

## 福岡

[APIシナリオテストを書くべき10の理由](https://www.docswell.com/s/katzumi/5EN8N1-10-reasons-to-write-api-scenario-tests)

<QRCode width="180" height="180" value="https://www.docswell.com/s/katzumi/5EN8N1-10-reasons-to-write-api-scenario-tests" color="4329B9" />


::right::

## 沖縄

[ActiveRecordパターンの呪縛を学びほぐして挑むクリーンアーキテクチャへの入り口](https://www.docswell.com/s/katzumi/Z989R9-activerecord-pattern-unlearning-clean-architecture)

<QRCode width="180" height="180" value="https://www.docswell.com/s/katzumi/Z989R9-activerecord-pattern-unlearning-clean-architecture" color="4329B9" />


---
layout: end
---

ご清聴ありがとうございました
