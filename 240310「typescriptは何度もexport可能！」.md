今日からtypescriptを使ったプロジェクトが始まった。

componentをexport defaultで既にexportしたら

typeはどうしょう？毎ファイルごとに作らないといけないのか？

![image](https://github.com/mocking-tiger/RAKUGAKI/assets/151588293/d9311115-9cc2-454a-ac94-be1585f293bc)

今日新しく分かったのはtypescriptでは、もうexport defaultで何かをexportしたといっても、

関数、変数、タイプ、インターフェースなど、何でも多くのexportができる。

例えば、a.tsxでDashboardsというタイプを作ったら、このタイプのpropsを渡したcomponentでは

![image](https://github.com/mocking-tiger/RAKUGAKI/assets/151588293/9f890ccf-953d-413a-9a1c-2a3cdb120aaf)

このように使うことができる。

ほんの少しだけだが、毎日少しずつtypescriptについて知っていくのが楽しくなっている。
