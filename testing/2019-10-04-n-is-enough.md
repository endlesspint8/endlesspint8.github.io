---
layout: post
title: To bar, or not to bar - what is the intention
subtitle: Ponying Up to a 'Simply Complexity' Example
tags: ["complexity", "simulation"]
shortlink: 
image: http://endlesspint.com/gallery/2018/beer-prplxd/pr_links.png
sideof: ["Second level beers", "http://eepurl.com/cj8urH", " into top PR style (grandparent sytles)."]
---

## More Dat

source(s): 
* https://yonaba.github.io/2012/08/14/List-your-GitHub-projects-using-JavaScript-and-jQuery.md.html
* https://jsfiddle.net/8p3ftmuh/2/
* https://www.keycdn.com/support/inline-small-css-and-javascript


<style>
.checkbox-grid li {
  display: block;
  float: left;
  width: 25%;
}
</style>




<input id="total" readonly>

<ul class="checkbox-grid">
  <li><input type="checkbox" name="text1" value="100" /><label for="text1">Text 1</label></li>
  <li><input type="checkbox" name="text2" value="110" /><label for="text2">Text 2</label></li>
  <li><input type="checkbox" name="text3" value="235" /><label for="text3">Text 3</label></li>
  <li><input type="checkbox" name="text4" value="554" /><label for="text4">Text 4</label></li>
  <li><input type="checkbox" name="text5" value="785" /><label for="text5">Text 5</label></li>
  <li><input type="checkbox" name="text6" value="111" /><label for="text6">Text 6</label></li>
  <li><input type="checkbox" name="text7" value="962" /><label for="text7">Text 7</label></li>
  <li><input type="checkbox" name="text8" value="474" /><label for="text8">Text 8</label></li>
</ul>

<script src="http://ajax.microsoft.com/ajax/jquery/jquery-2.1.3.min.js" type="text/javascript"></script>
<script type="text/javascript">
    $('input:checkbox').change(function ()
    {
          var total = 0;
          $('input:checkbox:checked').each(function(){
           total += isNaN(parseInt($(this).val())) ? 0 : parseInt($(this).val());
          });   
          $("#total").val(total);
    });
</script>



