# s_html_hamburgurnav_ozeki01
めっちゃ簡単・シンプルな右から出てくるハンバーガーメニュー、汎用性◎

https://zarigani-design-office.com/technology/humberger_btn/

https://zarigani-design-office.com/technology/drawer_menu/

## html
navの方はul以下特に指定なし、好きに組んでOK

```
    <!-- ここから -->
    <div class="nav">
      <button type="button" class="btn_menu sp">
        <span class="bar bar1"></span>
        <span class="bar bar2"></span>
        <span class="bar bar3"></span>
        <span class="menu">MENU</span>
        <span class="close">CLOSE</span>
      </button>
      <nav class="head_nav">
        <ul class="flex l_1 fz_14">
          <li><a href="#">ホーム</a></li>
          <li><a href="#">ニュース</a></li>
          <li><a href="#">オンラインショップ</a></li>
          <li><a href="#">ご利用方法</a></li>
          <li><a href="#">コンセプト＆ストーリー</a></li>
          <li><a href="#">ブログ</a></li>
          <li><a href="#/">お問合せ</a></li>
        </ul>
      </nav>
　 <!-- ここまで -->
  
```

## js

```
//ハンバーガーメニュー
  $(function(){
    $('.btn_menu').click(function(){
      $(this).toggleClass('active');
      $('.head_nav').toggleClass('open');}
    });
  })
```

## css
PCはレイアウトに合わせてnavを調整、buttonは隠しておけばOK
SPも下記だけが必須、あとは好きにレイアウト整える

```
@include media(767px) {
  /*   ボタンタグ設定   */
  button {
    display: block;
    background: none;
    border: none;
    padding: 0;
    width: 42px;
    color: #333;
    letter-spacing: 0.1em;
    cursor: pointer;
    position: fixed;
    top: 20px;
    right: 20px;
    z-index: 1001;
    text-align: center;
    outline: none;
    font-size: 10px;
  }
  /*   ハンバーガーボタン3本線   */
  button span.bar {
    display: block;
    height: 2px;
    background-color: #333;
    margin: 10px 0;
    transition: all 0.2s;
    transform-origin: 0 0;
  }
  button .close {
    letter-spacing: 0.08em;
    display: none;
  }
  button .menu {
    display: block;
  }
  /*  メニューアクティブ時  */
  button.active span.bar {
    width: 49px;
  }
  button.active .bar1 {
    transform: rotate(30deg);
  }
  button.active .bar2 {
    opacity: 0;
  }
  button.active .bar3 {
    transform: rotate(-30deg);
  }
  button.active .menu {
    display: none;
  }
  button.active .close {
    display: block;
  }
  /*  メニュー  */
  .head_nav {
    width: 312px;
    height: 100%;
    transition: all 0.2s;
    transform: translate(312px);
    position: fixed;
    top: 0;
    right: 0;
    z-index: 1000;
    background-color: #FFF;
  }
  /*  メニューアクティブ時  */
  .head_nav.open {
    transform: translate(0);
  }
/*　以下、個別にレイアウト調整　*/
    .nav{
      ul{
        padding:100px 0;
        text-align: center;
      }
      li{
        width: 100%;
        margin-bottom: 20px;
      }
    }
}
