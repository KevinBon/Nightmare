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
fncUpdateRunningTotal: function(){
		var curTotal = 0;
		var subtotalA = 0;
		var subtotalB = 0;
		var subtotalC = 0;
		$('div.form-horizontal *').filter(':input').each(function(){
			if(this.value != '' && this.value != 'Y' && this.value != 'y' && this.value != 'N' && this.value != 'n' && this.value != 0){
				if(/\d+_price/.test(this.id)) {
					if (!$(this).hasClass( "package" )) {
						curTotal += parseFloat(this.value || 0);
					}
				}
				if($(this).hasClass("dataGroupA")){
					subtotalA += parseFloat(this.value || 0);
				}
				if($(this).hasClass("dataGroupB")){
					subtotalB += parseFloat(this.value || 0);
				}
				if($(this).hasClass("dataGroupC")){
					subtotalC += parseFloat(this.value || 0);
				}
			}
		});
		if(curTotal != 0){
			$("#jsCalcTotal").html("Total: $"+ curTotal.toFixed(2));
		}
		if(subtotalA == 0){
			$("#A_subtotal").html("");
		}else{
			$("#A_subtotal").html(" $"+ subtotalA.toFixed(2));
		}
		if(subtotalB == 0){
			$("#B_subtotal").html("");
		}else{
			$("#B_subtotal").html(" $"+ subtotalB.toFixed(2));
		}
		if(subtotalC == 0){
			$("#C_subtotal").html("");
		}else{
			$("#C_subtotal").html(" $"+ subtotalC.toFixed(2));
		}
	},
});
```
