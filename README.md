
<h1>Add ssl sertificate to openserver local development</h1>
<h2>Install mksert ( https://github.com/FiloSottile/mkcert )</h2>

<ol>
   <li>Open Windows PowerShell (admin rules) and run <code>Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')</code></li>
   <li>Run <code>scoop bucket add extras</code></li>
   <li>Run <code>scoop install mkcert</code></li>
   <li>Run <code>mkcert -install</code></li>
</ol>
<hr>
<h2>Create single site ssl sertificate</h2>
<ul>
   <li>Run <code>mkcert example.com</code></li>
   <li>Two .pem files will be created at <code>C:\Windows\System32</code></li>
   <li>Copy this two files to project root and rename to .srt & .key (site.crt) and (site.key)</li>
   <li>Click site.crt and install</li>
   <li>Create _vhost.conf file in project root and copy code from OSPanel\userdata\config\Apache_2.4-PHP_7.2-7.3_vhost</li>
   <li>Replace SSLCertificateFile & SSLCertificateKeyFile lines, should be like <code>SSLCertificateFile SSLCertificateFile  "%hostdir%/site.crt"</code> and <code>SSLCertificateKeyFile "%hostdir%/site.key"</code></li>
   <li>Restart OpenServer</li>
   <li>In project config you should change http: to https: like <code>define('HTTPS_SERVER', 'https://site.com.ua/');</code> </li>
   <li>Run site with https like <code>https://site</code></li>
</ul>
<hr>