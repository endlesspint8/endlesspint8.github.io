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
  width: 50%;
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
  <li><input type="checkbox" name="Kentucky_Toppling1" value="3" /><label for="Kentucky_Toppling1">Kentucky Brunch Brand Stout - Toppling Goliath Brewing Company, 12.00%</label></li>
<li><input type="checkbox" name="Bourbon_Goose9" value="2.41875" /><label for="Bourbon_Goose9">Bourbon County Brand Coffee Stout - Goose Island Beer Co., 12.90%</label></li>
<li><input type="checkbox" name="Pliny_Russian7" value="2.5625" /><label for="Pliny_Russian7">Pliny The Younger - Russian River Brewing Company, 10.25%</label></li>
<li><input type="checkbox" name="Mornin'_Toppling8" value="3" /><label for="Mornin'_Toppling8">Mornin' Delight - Toppling Goliath Brewing Company, 12.00%</label></li>
<li><input type="checkbox" name="Pliny_Russian15" value="3" /><label for="Pliny_Russian15">Pliny The Elder - Russian River Brewing Company, 8.00%</label></li>
<li><input type="checkbox" name="Fundamental_Bottle12" value="2.68125" /><label for="Fundamental_Bottle12">Fundamental Observation - Bottle Logic Brewing, 14.30%</label></li>
<li><input type="checkbox" name="Bourbon_Goose24" value="2.85" /><label for="Bourbon_Goose24">Bourbon County Brand Stout - Goose Island Beer Co., 15.20%</label></li>
<li><input type="checkbox" name="Bourbon_Goose36" value="2.79375" /><label for="Bourbon_Goose36">Bourbon County Brand Vanilla Stout - Goose Island Beer Co., 14.90%</label></li>
<li><input type="checkbox" name="Zenne_325" value="2.625" /><label for="Zenne_325">Zenne Y Frontera - 3 Fonteinen, 7.00%</label></li>

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



