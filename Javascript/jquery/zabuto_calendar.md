# Zabuto Calendar

## Zabuto  Calendarとは

Twitter Bootstrapを使いカレンダーを表示できるjQueryプラグイン

下記のコードを使いカレンダーを初期化する

```js
<div id="my-calendar"></div>

<script type="application/javascript">
    $(document).ready(function () {
        $("#my-calendar").zabuto_calendar({language: "en"});
    });
</script>
```

## 設定

- language(string) カレンダーの言語を設定する。jpと設定すると日本語になる
- year(integer) 現在の年とは異なる年のカレンダーを初期化する
- month(integer) 現在の月とは異なる月でカレンダーを初期化する
- today(boolean) 今日の日を特別なバッジを表示する
- weekstartson(integer)
- legend 凡例を追加する。凡例は、指定された形式のオブジェクトの配列で構成される
```js
{type: string, label: string, badge: string, list: array}
```

## onclick アクション

特定の日にonclickイベントがトリガーされたときに実行する関数をカレンダーに追加できる

```js
$("#my-calendar").zabuto_calendar( { action: function() { myDateFunction(this.id); } } );
```

日付を取得するには、カレンダーの日付idを使用し、要素情報にアクセスする

```js
function myDateFunction(id) {
    var date = $("#" + id).data("date");
    var hasEvent = $("#" + id).data("hasEvent");
}
```

使用例

```js
$(document).ready(function () {
        let $baseUrl = '{{ url("/calendar",$data->カレンダーCD)}}';
        $("#calendar").zabuto_calendar({
            language: "jp",
            weekstartson:0,
             legend: [
                {type: "block", label: "休日", classname: "event-1"},
                {type: "block", label: "指定休日", classname: "event-2"},
            ],
            ajax:{
                url: $baseUrl + "/month",
            },
            action:function(){
                let $this = $("#" + this.id);
                let date = $this.data("date");
                let nextStatus = 0 ;
                var $dayElement = $('#' + this.id + '_day');
                if($this.find(".event-2").length!==1){
                    if ($this.find(".event-1").length!==1){
                        nextStatus = 1;
                        $($this).addClass('event-styled')
                        $($dayElement).addClass('event-'+nextStatus);
                    }else{
                            nextStatus = 2;
                            $($dayElement).removeClass('event-1');
                            $($dayElement).addClass('event-'+nextStatus);
                    }
                }else{
                    $($dayElement).removeClass('event-2'); 
                }
                
                $.ajax({
                    url: $baseUrl + "/day/" + date,
                    data: {"status":nextStatus,"_token":$("input[name='_token']").val()},
                    type:"POST",
                    datatype:"json",
                    success:function(){
                        alert("更新できた");
                    },
                    error:function(){
                        alert("あかんやった");
                    }
                });  
                return;
            },
        }); 
    });
```

### 参考

[zabuto / calendar：このライブラリは、Webページに月間カレンダーを追加できるBootstrap用のjQueryプラグインです。](https://github.com/zabuto/calendar)

[jQueryプラグイン \- Bootstrapを使ったカレンダーを実装 \- Zabuto Calendar](https://webkaru.net/jquery-plugin/zabuto-calendar/)