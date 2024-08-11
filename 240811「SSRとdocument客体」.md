![image](https://github.com/user-attachments/assets/ee3f9b55-b7d2-48e3-9df6-07740a0d8a0f)

vercelのデプロイがずっと失敗して、初めての失敗がいつからかを探してみたら
カスタムフックでmodalを作ってからだった。

---

![image](https://github.com/user-attachments/assets/b5f371a3-5c6f-407c-a4ee-f3cad3200560)

エラーログをみたら/dashboard/todo-allでdocument is not definedというエラーができたって、

todo-allのファイルにはdocument客体を参照しているコードがなかった。

---

![image](https://github.com/user-attachments/assets/308129d3-3925-45f7-b27b-4cee2c3eb1e6)

useModalにはreactDOMのcreatePortalを使ってmodalを作っているんだけど

作られる所がdocument.bodyなので、サーバーにはdocumnet客体が無いから

SSR環境ではエラーできたんだ。

---

![image](https://github.com/user-attachments/assets/1327b828-6595-4948-b553-8d226b5c79f0)

documentがなければnullを返還させる条件問を追加して、改めてデプロイすると、

---

![image](https://github.com/user-attachments/assets/64e5e656-444f-4877-bcd6-89c68dc85080)

よくできました。
今日もひとつ教わった！
