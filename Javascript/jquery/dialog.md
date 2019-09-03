# dialog

ダイアログの中身

```php
<div>
<form method="get" action="{{route('site.search')}}" class="form-inline query">
    <div class="form-group">
        <input type="text" name="現場名" id="現場名" class="form-control" value="{{$cdname}}"
                    placeholder="現場名" maxlength="40">
    </div>
    <div class="button-group">
        <button type="submit" class="form-control btn-secondary">検索</button>
    </div>
</form>

<div class="searcharea">
    <div class="table-responsive-sm">
        <table class="table table-striped table-bordered">
            <thead class="thead-light">
                <tr>
                    <th><a href="javascript:void(0);" target="_self">現場CD</a></th>
                    <th><a href="javascript:void(0);" target="_self">現場名</a></th>
                </tr>
            </thead>
            <tbody>
                @foreach($datas as $data)
                <tr>
                    <td>{{$data->現場CD}}</td>
                    <td><a href="javascript:void(0);" class="selectable" data-id="{{$data->現場CD}}">{{$data->現場名}}</a></td>
                </tr>
                @endforeach
                {{$datas->appends(['現場名'=>$cdname,'select_lists'=>$datas->perPage()])->links()}}
            </tbody>
        </table>
        {{$datas->appends(['現場名'=>$cdname,'select_lists'=>$datas->perPage()])->links()}}
    </div>
</div>
</div>
```

ダイアログの外側

```js
<div class="modal fade" id="siteDialog" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle"
    aria-hidden="true">
    <div class="modal-dialog" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalCenterTitle">現場検索</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
            </div>
        </div>
    </div>
</div>
<script type="text/javascript">
    if (!skipjack) var skipjack = {} ;

$(function(){
    skipjack.siteDialog = {
        initUrl : "{{route('site.search')}}",
        open : function(callbackFunc){
            $("#siteDialog").data("currentCallback",callbackFunc);
            $.ajax({
                type: "GET",
                url: this.initUrl,
                success: function (html) {
                    $("#siteDialog .modal-body").html(html);
                    $("#siteDialog").modal("show");
                }
            });
        },
    };
    $("#siteDialog").on("click",".selectable",function(){
        var callback = $("#siteDialog").data("currentCallback");
        $("#siteDialog").modal("hide");
        callback($(this).data("id"),$(this).html());
    });
    $("#siteDialog .modal-body").on("submit","form.query",function(){
        $.ajax({
            type: "GET",
            url: $(this).attr("action") + "?" + $(this).serialize(),
            success: function (html) {
                $("#siteDialog .modal-body").html(html);
            }
        });
        return false;
    });
    $("#siteDialog .modal-body").on("click",".page-link",function(){
        $.ajax({
            type: "GET",
            url: $(this).attr("href") ,
            success: function (html) {
                $("#siteDialog .modal-body").html(html);
            }
        });
        return false;
    });
});

</script>
```

## 表示

```js
skipjack.siteDialog = {
    initUrl : "{{route('site.search')}}",
    open : function(callbackFunc){
        $("#siteDialog").data("currentCallback",callbackFunc);
        $.ajax({
            type: "GET",
            url: this.initUrl,
            success: function (html) {
                $("#siteDialog .modal-body").html(html);
                $("#siteDialog").modal("show");
            }
        });
    },
};
```

## 取得

```js
$("#siteDialog").on("click",".selectable",function(){
    var callback = $("#siteDialog").data("currentCallback");
    $("#siteDialog").modal("hide");
    callback($(this).data("id"),$(this).html());
});
```

## ダイアログ内の検索

```js
$("#siteDialog .modal-body").on("submit","form.query",function(){
    $.ajax({
        type: "GET",
        url: $(this).attr("action") + "?" + $(this).serialize(),
        success: function (html) {
            $("#siteDialog .modal-body").html(html);
        }
    });
    return false;
});
```

`return false;`がないと元のページが表示させる。

## ダイアログ内のページネーション 

```js
$("#siteDialog .modal-body").on("click",".page-link",function(){
    $.ajax({
        type: "GET",
        url: $(this).attr("href") ,
        success: function (html) {
            $("#siteDialog .modal-body").html(html);
        }
    });
    return false;
});
```

```php
<form method="post" action={{route($route)}} name="report">
@csrf
    <div id="app"> 
        <details-component :data="{{json_encode($data->toArray(),JSON_UNESCAPED_UNICODE)}}" :datails="{{json_encode($data->datails->toArray(),JSON_UNESCAPED_UNICODE)}}" :mode="{{json_encode($mode,JSON_UNESCAPED_UNICODE)}}"></details-component>
    </div>
</form>
@include("site.dialog")
```

```js
sitedialog() {
	let $this = $(this);
	skipjack.siteDialog.open(function(id, name) {
		$("#sitecd").val(id);
		$("#sitename").val(name);
	});
},
```

`let $this = $(this);`は呼び出し元をローカル変数にとっておく