
# Demo

----


<div>
  <label>Inflated + Base64-Decoded (Original): <span id="len-inflated"></span></label>
  <textarea id="inflated" cols="64" rows="10"></textarea>
</div>
<div>
  <button type="button" id="btn-deflate">Deflate</button>
  <button type="button" id="btn-inflate">Inflate</button>
</div>
<div>
  <label>Deflated + Base64-Encoded (Compressed): <span id="len-deflated"></span></label>
  <textarea id="deflated" cols="64" rows="6"></textarea>
</div>

````js
seajs.use(['../rawdeflate', '../rawinflate', '../base64'], function(Deflate, Inflate, Base64){

  var $ = function(id){ return document.getElementById(id) };

  var iptInflated = $('inflated');
  var iptDeflated = $('deflated');

  function updateInfo(){
    $('len-inflated').innerHTML = iptInflated.value.length;
    $('len-deflated').innerHTML = iptDeflated.value.length;
  }
  $('inflated').onkeyup = function(evt) {
    iptDeflated.value = Base64.toBase64(Deflate(Base64.utob(this.value)));
    updateInfo();
  };
  $('deflated').onkeyup = function(evt) {
    $('inflated').value = Base64.btou(Inflate(Base64.fromBase64(this.value)));
    updateInfo();
  }
})
````
