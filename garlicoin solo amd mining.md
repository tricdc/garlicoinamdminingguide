---


---

<h1 id="garlicoin-solo-amd-mining">garlicoin solo amd mining</h1>
<h2 id="windows-10">Windows 10</h2>
<ol>
<li>Get <a href="https://docs.microsoft.com/en-us/windows/wsl/install-win10">Windows Subsystem for Linux</a></li>
<li>Start a garlicoind running on rpc port 42070 with username test and password test.</li>
<li>Open bash and run <code>cd</code></li>
<li>Run <code>curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash</code></li>
<li>Run <code>logout</code> and reopen bash</li>
<li>Run <code>nvm install 0.10.25</code> and then <code>nvm use 0.10.25</code></li>
<li>Run <code>sudo apt-get install nano python-dev build-essential libssl-dev</code> and install the packages.</li>
<li>Follow <a href="https://redis.io/topics/quickstart">these</a> instructions for installing Redis</li>
<li>Run <code>git clone https://github.com/zone117x/node-open-mining-portal.git nomp</code></li>
<li>Run <code>cd nomp</code></li>
<li>Run <code>nano package.json</code> and change the following:</li>
</ol>
<blockquote>
<p>“request”: “<strong>*</strong>” -&gt; “request”: “<strong>2.81.0</strong>”</p>
</blockquote>
<ol start="12">
<li>Press ctrl+x then y and then enter to save and exit</li>
<li>Run <code>npm update</code></li>
<li>Run <code>cd coins</code></li>
<li>Run <code>nano garlicoin.json</code></li>
<li>Paste <a href="https://pastebin.com/raw/9k3Qa5t4">this</a> and save and exit nano</li>
<li>Run <code>cd ..</code></li>
<li>Run <code>nano config.json</code></li>
<li>Paste <a href="https://pastebin.com/raw/hvJagkrw">this</a> and save and exit nano</li>
<li>Run <code>cd pool_configs</code></li>
<li>Run <code>nano garlicoin.json</code></li>
<li>Paste <a href="https://pastebin.com/raw/FJuup0uc">this</a> and change the bold to your garlicoin address:</li>
</ol>
<blockquote>
<p>“address”: “<strong>mzJeLWYDTwimZuV9CiYKVH5h2QJ4uRXTj6</strong>”</p>
</blockquote>
<ol start="23">
<li>Save and exit nano</li>
<li>Run <code>cd ..</code></li>
<li>Run <code>node init.js</code></li>
<li>Now set your yacminer command to something like except use your address instead of mine:</li>
</ol>
<blockquote>
<p>yacminer --nscrypt --nfmin 10 --nfmax 10 -o stratum+tcp://<strong>127.0.0.1:3333</strong> -u mzJeLWYDTwimZuV9CiYKVH5h2QJ4uRXTj6 -p x -T -I 15</p>
</blockquote>

