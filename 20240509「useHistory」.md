useHistoryは最新のreact-router-domでは支援されねいない。

ユーザーは掲示物を見ている時、

ログインが必要な機能を選んだらログインページへ移動して

ログインした後また見ていた掲示物に戻ってくれる機能が作りたかった。

---

![image](https://github.com/mocking-tiger/RAKUGAKI/assets/151588293/9b42a2aa-d08c-4d96-9faa-04bffbe9cc62)

useHitoryは最新のreact-router-domでは支援されてないのでuseNavigateを使ったほうがいい。
```
const navigate = useNavigate();
navgate(-1)
```
このように値を-1にすると以前のページに行くことができる。

---

![image](https://github.com/mocking-tiger/RAKUGAKI/assets/151588293/5b9b12e2-5d0f-4dc6-8449-3378bd0b87cf)

ログインしてない状態で「予約する」をクリックしたら

---

![image](https://github.com/mocking-tiger/RAKUGAKI/assets/151588293/b443446b-3491-4e5f-b10f-2967de94f2e6)

modalでログインページに行くかどうかを聞く。

---

![image](https://github.com/mocking-tiger/RAKUGAKI/assets/151588293/4dd382a3-ca29-4e45-975c-24f71e7520a5)

ログインすると、

---

![image](https://github.com/mocking-tiger/RAKUGAKI/assets/151588293/fa0c72e4-ba0c-4caf-bbb8-f655623e6194)

先のページに着いた！

---

これはいつも以前のページに送ってしまうので案外の動作をするかも知らない。
（urlなどを通って直接に接近した場合など）

こんな場合のため条件をかける必要があるが、これは次に扱ってみる。
