# Timer-easy


<html lang="ja">
    <head>
        <meta charset="utf-8">
        <title>タイマー</title>
    </head>
<body>
    <div id="timer"></div>
    <script language="javascript">
        document.addEventListener('DOMContentLoaded',function(){},false);
        var Timer=function(sst,set,em,opd){
            this.sst=sst;
            this.set=set;
            this.em='終了！';
            this.opd='timer';
            //document.write(this.sst,this.set,this.em,this.opd);
        };
        
        //Timer.prototype.countDown=function(){}
        function calculateTime() {
            var sst = new Date(this.sst);  // セール開始日時
            var set = new Date(this.set);  // セール終了日時
 
            // タイマーを表示する対象要素
            var countDownTimer = document.getElementById(this.opd);
 
            var em = this.em;  // セール終了時のメッセージ
            var ctCD;  // 現在時刻
            var ust;  // 開始時刻までの残り時間
            var uft;  // 終了時刻までの残り時間
            var oneDay = 24 * 60 * 60 * 1000;  // 一日をミリ秒で表現した数値
            var d = 0;  // 日
            var h = 0;  // 時
            var m = 0;  // 分
            var s = 0;  // 秒

        //function calculateTime() {
            ctCD = new Date();
            var c=ctCD.getTime();
            var a=sst.getTime();
            var b=set.getTime();
            ust = a - c;
            uft = b - c;
            var us=Math.abs(ust);
            var uf=Math.abs(uft);
 
            if (c < a) {
                d = Math.floor(us / oneDay);
                h = Math.floor((us % oneDay) / (60 * 60 * 1000));
                m = Math.floor((us % oneDay) / (60 * 1000)) % 60;
                s = Math.floor((us % oneDay) / 1000) % 60 % 60;
            } else {
                d = Math.floor(uf / oneDay);
                h = Math.floor((uf % oneDay) / (60 * 60 * 1000));
                m = Math.floor((uf % oneDay) / (60 * 1000)) % 60;
                s = Math.floor((uf % oneDay) / 1000) % 60 % 60;
            }
            if (c < a) {
                countDownTimer.innerHTML='開始まで'+ d + '日' + h + '時間' + m + '分' + s + '秒';
            } else if (c >= a && c <= b) {
                countDownTimer.innerHTML='あと' + d + '日' + h + '時間' + m + '分' + s + '秒' + 'で終了';
            } else {
                countDownTimer.innerHTML =em;
            }

            //showTime();
        }

        //function showTime() {
          //  if (c < a) {
            //    countDownTimer.innerHTML='開始まで'+ d + '日' + h + '時間' + m + '分' + s + '秒';
            //} else if (c >= a && c <= b) {
              //  countDownTimer.innerHTML='あと' + d + '日' + h + '時間' + m + '分' + s + '秒' + 'で終了';
            //} else {
              //  countDownTimer.innerHTML =em;
            //}
        //}

        setInterval('calculateTime()', 1000);
        var myTimer=Timer('2021/9/5 6:00:00', '2021/9/10 00:00:00',  '終了！', 'timer');
        myTimer.countDown();
    </script>
</body>
</html>
