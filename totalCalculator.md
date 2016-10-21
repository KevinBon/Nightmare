```html
<!-- Article item line -->
<div class="form-group">
  <div class="col-lg-1 col-md-1 col-sm-1">
    <input class="form-control" type="text" id="58363_ledger_code" value="13" disabled="">
  </div>
  <div class="col-sm-1">
  </div>
  <div class="col-sm-4">
    <div class="contractformsetmarginleft">
      <input class="form-control" type="text" data-type="label" data-linetype="2" id="58363_label" value="Article XXX" disabled="">
    </div>
  </div>
  <div class="col-sm-1">
    <input class="dataGroupA form-control package" type="text" id="58363_price" value="5300"></div>
  </div>
</div>
<!-- ... -->
```

```js
var curTotal = 0;
var subtotalA = 0;
var subtotalB = 0;
var subtotalC = 0;
$('div.form-horizontal *').filter(':input').each(function(){
  if(!isNaN(this.value)){ // if is number -> true
    if(/\d+_price/.test(this.id)) {
      if (!$(this).hasClass( "package" )) {
        curTotal += parseFloat(this.value);
      }
    }
    if($(this).hasClass("dataGroupA")){
      subtotalA += parseFloat(this.value);
    }
    if($(this).hasClass("dataGroupB")){
      subtotalB += parseFloat(this.value);
    }
    if($(this).hasClass("dataGroupC")){
      subtotalC += parseFloat(this.value);
    }
  }
});
```
