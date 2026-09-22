# Lab: what the site can do

[!INCLUDE [content-disclaimer](../includes/content-disclaimer.md)]

Test page for components available with the current template (DocFX 2.80, Bootstrap 3, jQuery). Not linked from the navigation.

## 1. Carousel (slider)

<div id="mm-carousel" class="carousel slide" data-ride="carousel" data-interval="6000">
  <ol class="carousel-indicators">
    <li data-target="#mm-carousel" data-slide-to="0" class="active"></li>
    <li data-target="#mm-carousel" data-slide-to="1"></li>
    <li data-target="#mm-carousel" data-slide-to="2"></li>
  </ol>
  <div class="carousel-inner" role="listbox">
    <div class="item active"><div class="mm-slide"><h3>Next call: October 20, 2026</h3><p>Modern Compliance in Microsoft 365, with Joanne Klein, MVP.</p><a class="btn btn-primary" href="https://aka.ms/mm4m365/invite">Join</a></div></div>
    <div class="item"><div class="mm-slide"><h3>New: Security competency</h3><p>Two years in the making. Most organizations are at level 200 and don't know it.</p><a class="btn btn-default" href="../competencies/microsoft365-maturity-model-security.md">Read it</a></div></div>
    <div class="item"><div class="mm-slide"><h3>Run a quick assessment</h3><p>Score your organization in one sitting with the workshop workbook.</p><a class="btn btn-default" href="../tools-samples/microsoft365-maturity-model--run-workshop.md">How to</a></div></div>
  </div>
  <a class="left carousel-control" href="#mm-carousel" role="button" data-slide="prev"><span class="glyphicon glyphicon-chevron-left"></span></a>
  <a class="right carousel-control" href="#mm-carousel" role="button" data-slide="next"><span class="glyphicon glyphicon-chevron-right"></span></a>
</div>

## 2. Tabs (DocFX syntax)

# [Level 100](#tab/l100)
Initial. It's switched on. Ad hoc, reactive, person-dependent.
# [Level 300](#tab/l300)
Defined. Documented, repeatable, owned. The level every competency should reach.
# [Level 500](#tab/l500)
Optimizing. Continuous improvement with feedback loops. Never finished.
---

## 3. Accordion (collapse)

<div class="panel-group" id="mm-acc">
  <div class="panel panel-default"><div class="panel-heading"><h4 class="panel-title"><a data-toggle="collapse" data-parent="#mm-acc" href="#acc1">What is a competency?</a></h4></div>
  <div id="acc1" class="panel-collapse collapse in"><div class="panel-body">A business capability area, described at five levels. Thirteen are published.</div></div></div>
  <div class="panel panel-default"><div class="panel-heading"><h4 class="panel-title"><a data-toggle="collapse" data-parent="#mm-acc" href="#acc2">Do I need Microsoft 365 E5?</a></h4></div>
  <div id="acc2" class="panel-collapse collapse"><div class="panel-body">No. The model describes capability, not licences. You can reach level 300 without E5.</div></div></div>
</div>

## 4. PDF hosted in the repo, embedded

<iframe class="mm-pdf" src="files/sample-deck.pdf#toolbar=0&view=FitH" title="Sample deck"></iframe>

<p><a class="btn btn-default" href="files/sample-deck.pdf" download>Download PDF</a></p>

## 5. PowerPoint viewed online (file stays in the repo, no download needed)

<iframe class="mm-office" src="https://view.officeapps.live.com/op/embed.aspx?src=https%3A%2F%2Fpnp.github.io%2Fmaturity-model%2Fcompetencies%2Fimages%2Fmicrosoft365-maturity-model--management-of-content%2FManagement%2520of%2520Content%2520-%2520Content%2520Lifecycle.pptx" title="Content Lifecycle"></iframe>

## 6. YouTube playlist, whole playlist in one player

<div class="mm-video"><iframe src="https://www.youtube-nocookie.com/embed/videoseries?list=PLR9nK3mnD-OXALeeIt1nbgBcSLj3WxyBi" title="MM4M365 recordings" allowfullscreen></iframe></div>

## 7. Interactive quick self-assessment (runs in the browser, nothing is sent anywhere)

<div id="mm-quiz" class="mm-card">
<p>Rate your organization 1 to 5 on four competencies:</p>
<label>Collaboration <input type="range" min="1" max="5" value="2" data-c="Collaboration"></label><br>
<label>Communication <input type="range" min="1" max="5" value="3" data-c="Communication"></label><br>
<label>Security <input type="range" min="1" max="5" value="2" data-c="Security"></label><br>
<label>Staff &amp; Training <input type="range" min="1" max="5" value="1" data-c="Staff & Training"></label>
<canvas id="mm-radar" width="400" height="300"></canvas>
</div>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
<script>
(function(){var inputs=document.querySelectorAll('#mm-quiz input');var ctx=document.getElementById('mm-radar');
var chart=new Chart(ctx,{type:'radar',data:{labels:[].map.call(inputs,function(i){return i.dataset.c}),datasets:[{label:'Level (x100)',data:[].map.call(inputs,function(i){return +i.value}),fill:true}]},options:{scales:{r:{min:0,max:5,ticks:{stepSize:1}}}}});
inputs.forEach(function(i){i.addEventListener('input',function(){chart.data.datasets[0].data=[].map.call(inputs,function(x){return +x.value});chart.update();});});})();
</script>
