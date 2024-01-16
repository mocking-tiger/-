setTimeoutは、JAVASCRIPTの非同期処理を説明するとき

挙げられる代表的な機能の中で一つである。

    setTimeout(function(){
      console.log("hello world");
    }, 2000);

基本的に上のような姿をしている。

一番目のパラメーターで動作する関数を、

二番目で遅延させる時間をミリ秒でもらう。

つまり、上のsetTimeoutはconsole.log('hello world')を

２０００ミリ秒（2秒）後で実行するコードである。

だたし、javascriptはシングルスレッドであるので、

もしcall stackが空いていなかったら、パラメーターで渡した時間より

長く掛かるかもしれない。

このcall stackやqueue,については次に整理しておく。