<h1 class="code-line" data-line-start=0 data-line-end=1 ><a id="Removero_API_0"></a>Removero API</h1>
<h2 class="code-line" data-line-start=1 data-line-end=2 ><a id="__Free___API_to_remove_background_from_your_photo_1"></a><strong>Free</strong> API to remove background from your photo</h2>
<p class="has-line-data" data-line-start="3" data-line-end="4"><a href="https://www.python.org/"><img src="https://www.python.org/static/img/psf-logo@2x.png" alt="Python Powered"></a></p>
<p class="has-line-data" data-line-start="5" data-line-end="6"><a href="https://removero.serveo.net/"><img src="https://raw.githubusercontent.com/fandercompany/removero-api/main/build.svg" alt="Build Status"></a></p>
<p class="has-line-data" data-line-start="7" data-line-end="8">Removero API is the fastest background removal API that handles almost any image and returns the image in the best quality.</p>
<ul>
<li class="has-line-data" data-line-start="9" data-line-end="10">Free</li>
<li class="has-line-data" data-line-start="10" data-line-end="11">Simple</li>
<li class="has-line-data" data-line-start="11" data-line-end="12">Site</li>
<li class="has-line-data" data-line-start="12" data-line-end="14">API</li>
</ul>
<h2 class="code-line" data-line-start=14 data-line-end=15 ><a id="Requirements_14"></a>Requirements</h2>
<p class="has-line-data" data-line-start="16" data-line-end="18">Dillinger is currently extended with the following plugins.<br>
Instructions on how to use them in your own application are linked below.</p>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th>Plugin</th>
<th>README</th>
</tr>
</thead>
<tbody>
<tr>
<td>RemBG</td>
<td>[<a href="https://pypi.org/project/rembg/">https://pypi.org/project/rembg/</a>]</td>
</tr>
<tr>
<td>Flask</td>
<td>[<a href="https://pypi.org/project/Flask/">https://pypi.org/project/Flask/</a>]</td>
</tr>
<tr>
<td>Werkzeug</td>
<td>[<a href="https://pypi.org/project/Werkzeug/">https://pypi.org/project/Werkzeug/</a>]</td>
</tr>
<tr>
<td>Requests</td>
<td>[<a href="https://pypi.org/project/requests">https://pypi.org/project/requests</a>]</td>
</tr>
</tbody>
</table>
<h2 class="code-line" data-line-start=26 data-line-end=27 ><a id="How_to_use_26"></a>How to use</h2>
<h4 class="code-line" data-line-start=27 data-line-end=28 ><a id="Python_example_27"></a>Python example</h4>
<p class="has-line-data" data-line-start="29" data-line-end="30">Install <code>request</code> for make request to API</p>
<pre><code class="has-line-data" data-line-start="32" data-line-end="34" class="language-sh">pip install requests
</code></pre>
<p class="has-line-data" data-line-start="35" data-line-end="36">Make a request</p>
<pre><code class="has-line-data" data-line-start="38" data-line-end="53" class="language-sh">import requests

url = <span class="hljs-string">'https://apiremovero.serveo.net/api/remove_background'</span>

with open(<span class="hljs-string">'anime.jpg'</span>, <span class="hljs-string">'rb'</span>) as image_file:
    files = {<span class="hljs-string">'image'</span>: image_file}
    response = requests.post(url, files=files)

    <span class="hljs-keyword">if</span> response.status_code == <span class="hljs-number">200</span>:
        result = response.json()
        result_filename = result[<span class="hljs-string">'result'</span>]
        <span class="hljs-built_in">print</span>(f<span class="hljs-string">'Result filename: {result_filename}'</span>)
    <span class="hljs-keyword">else</span>:
        <span class="hljs-built_in">print</span>(<span class="hljs-string">'Error occurred:'</span>, response.text)
</code></pre>
<h4 class="code-line" data-line-start=54 data-line-end=55 ><a id="JS_example_54"></a>JS example</h4>
<pre><code class="has-line-data" data-line-start="57" data-line-end="94" class="language-sh">const fetch = require(<span class="hljs-string">'node-fetch'</span>);
const fs = require(<span class="hljs-string">'fs'</span>);

const url = <span class="hljs-string">'https://apiremovero.serveo.net/api/remove_background'</span>;
const imageFilePath = <span class="hljs-string">'./anime.jpg'</span>;

fs.readFile(imageFilePath, (err, imageBuffer) =&gt; {
  <span class="hljs-keyword">if</span> (err) {
    console.error(<span class="hljs-string">'Error reading image:'</span>, err);
    <span class="hljs-built_in">return</span>;
  }

  const formData = new FormData();
  formData.append(<span class="hljs-string">'image'</span>, imageBuffer, { filename: <span class="hljs-string">'anime.jpg'</span> });

  fetch(url, {
    method: <span class="hljs-string">'POST'</span>,
    body: formData,
  })
    .then((response) =&gt; {
      <span class="hljs-keyword">if</span> (response.status === <span class="hljs-number">200</span>) {
        <span class="hljs-built_in">return</span> response.json();
      } <span class="hljs-keyword">else</span> {
        throw new Error(`Request failed with status <span class="hljs-variable">${response.status}</span>`);
      }
    })
    .then((result) =&gt; {
      const resultFilename = result.result;
      console.log(`result filename: <span class="hljs-variable">${resultFilename}</span>`);
    })
    .catch((error) =&gt; {
      console.error(<span class="hljs-string">'An error occurred:'</span>, error);
    });
});


</code></pre>
<h3 class="code-line" data-line-start=94 data-line-end=95 ><a id="Input_94"></a>Input</h3>
<p class="has-line-data" data-line-start="95" data-line-end="96"><a href="https://apiremovero.serveo.net/static/anime.jpg"><img src="https://apiremovero.serveo.net/static/anime.jpg" alt="Input"></a></p>
<h3 class="code-line" data-line-start=97 data-line-end=98 ><a id="Output_97"></a>Output</h3>
<p class="has-line-data" data-line-start="98" data-line-end="99"><a href="https://apiremovero.serveo.net/static/anime.jpg"><img src="https://apiremovero.serveo.net/static/result_anime.jpg" alt="output"></a></p>
