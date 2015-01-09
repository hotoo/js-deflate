
# Demo

----


<dl>
<dt>Inflated + Base64-Decoded (Original):</dt>
<dd><textarea id="inflated" cols="64" rows="10"></textarea></dd>
<dt>Deflated + Base64-Encoded (Compressed):</dt>
<dd><textarea id="deflated" cols="64" rows="5"></textarea></dd>
</dl>

````js
seajs.use(['../rawdeflate', '../rawinflate', '../base64'], function(Deflate, Inflate, Base64){

  var $ = function(id){ return document.getElementById(id) };

  $('inflated').onkeyup = function(evt) {
    $('deflated').value = Base64.toBase64(Deflate(Base64.utob(this.value)));
  };
  $('deflated').onkeyup = function(evt) {
    $('inflated').value = Base64.btou(Inflate(Base64.fromBase64(this.value)));
  }
})
````
