![image](https://github.com/user-attachments/assets/61dfae21-4fc7-454e-9732-643390b2b043)

trelloのクローンコーディングのプロジェクト。

---

![image](https://github.com/user-attachments/assets/11154e91-f175-4659-ae70-b13a9b057fe7)

ボードを削除して数が０になるといきなりスクロールが生じた。

---

![image](https://github.com/user-attachments/assets/dc8f5278-ad30-44fb-8914-7b40b647aba7)

スクロールを最後まで下げてみたら、どこからか「０」が出来た。

---

![image](https://github.com/user-attachments/assets/fe729a4d-cf65-4cbe-b0dc-7894f67de37b)

ネットで調べてみたら、あの＆＆を活用した条件部が問題だった。

自分がJAVASCRIPTのTRUTHYを使って、LENGTHが１以上であればDROPPABLEコンポネントをレンダリングしようとしてたが、

&& 比較式のばあい、左項の値がFALSYだったら左項をそのままリターンするのを忘れていたんだ。

つまり、左項の値がFALSY の場合を想定しなかったものである。

---

![image](https://github.com/user-attachments/assets/9793a912-41dc-4a5b-a627-37396020af0d)

こう修正して、いつもtrueでなければfalseだけをリターンさせたらスクロールが消えた！

![image](https://github.com/user-attachments/assets/765e5f13-ae24-4bfb-a585-f93e72afd47d)

