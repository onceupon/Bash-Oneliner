<a id="handy-bash-oneliner-commands-for-tsv-file-editing" class="anchor" href="#handy-bash-oneliner-commands-for-tsv-file-editing" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Handy Bash oneliner commands for tsv file editing

<ul>
<li><a href="#grep">Grep</a></li>
<li><a href="#sed">Sed</a></li>
<li><a href="#awk">Awk</a></li>
<li><a href="#xargs">Xargs</a></li>
<li><a href="#find">Find</a></li>
<li><a href="#loops">Loops</a></li>
<li><a href="#download">Download</a></li>
<li><a href="#random">Random</a></li>
<li><a href="#others">Others</a></li>
<li><a href="#system">System</a></li>
</ul>

<h2>
<a id="grep" class="anchor" href="#grep" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Grep</h2>

<h5>
<a id="extract-text-bewteen-words-eg-w1w2" class="anchor" href="#extract-text-bewteen-words-eg-w1w2" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>extract text bewteen words (e.g. w1,w2)</h5>

<div class="highlight highlight-source-shell"><pre>grep -o -P <span class="pl-s"><span class="pl-pds">'</span>(?&lt;=w1).*(?=w2)<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="grep-lines-without-word-eg-bbo" class="anchor" href="#grep-lines-without-word-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep lines without word (e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>grep -v bbo filename</pre></div>

<h5>
<a id="grep-only-onefirst-match-eg-bbo" class="anchor" href="#grep-only-onefirst-match-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep only one/first match (e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>grep -m 1 bbo filename</pre></div>

<h5>
<a id="grep-and-count-eg-bbo" class="anchor" href="#grep-and-count-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep and count (e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>grep -c bbo filename</pre></div>

<h5>
<a id="insensitive-grep-eg-bbobbobbo" class="anchor" href="#insensitive-grep-eg-bbobbobbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>insensitive grep (e.g. bbo/BBO/Bbo)</h5>

<div class="highlight highlight-source-shell"><pre>grep -i <span class="pl-s"><span class="pl-pds">"</span>bbo<span class="pl-pds">"</span></span> filename </pre></div>

<h5>
<a id="count-occurrence-eg-three-times-a-line-count-three-times" class="anchor" href="#count-occurrence-eg-three-times-a-line-count-three-times" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>count occurrence (e.g. three times a line count three times)</h5>

<div class="highlight highlight-source-shell"><pre>grep -o bbo filename </pre></div>

<h5>
<a id="color-the-match-eg-bbo" class="anchor" href="#color-the-match-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>COLOR the match (e.g. bbo)!</h5>

<div class="highlight highlight-source-shell"><pre>grep --color bbo filename </pre></div>

<h5>
<a id="grep-search-all-files-in-a-directoryeg-bbo" class="anchor" href="#grep-search-all-files-in-a-directoryeg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep search all files in a directory(e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>grep -R bbo /path/to/directory </pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>grep -r bbo /path/to/directory </pre></div>

<h5>
<a id="search-all-files-in-directory-only-output-file-names-with-matcheseg-bbo" class="anchor" href="#search-all-files-in-directory-only-output-file-names-with-matcheseg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>search all files in directory, only output file names with matches(e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>grep -Rh bbo /path/to/directory </pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>grep -rh bbo /path/to/directory </pre></div>

<h5>
<a id="grep-or-eg-a-or-b-or-c-or-d" class="anchor" href="#grep-or-eg-a-or-b-or-c-or-d" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep OR (e.g. A or B or C or D)</h5>

<pre><code>grep 'A\|B\|C\|D' 
</code></pre>

<h5>
<a id="grep-and-eg-a-and-b" class="anchor" href="#grep-and-eg-a-and-b" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep AND (e.g. A and B)</h5>

<div class="highlight highlight-source-shell"><pre>grep <span class="pl-s"><span class="pl-pds">'</span>A.*B<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="grep-all-content-of-a-filea-from-fileb" class="anchor" href="#grep-all-content-of-a-filea-from-fileb" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep all content of a fileA from fileB</h5>

<div class="highlight highlight-source-shell"><pre>grep -f fileA fileB </pre></div>

<h5>
<a id="grep-a-tab" class="anchor" href="#grep-a-tab" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep a tab</h5>

<div class="highlight highlight-source-shell"><pre>grep <span class="pl-s"><span class="pl-pds">$'</span><span class="pl-cce">\t</span><span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="grep-variable-from-variable" class="anchor" href="#grep-variable-from-variable" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep variable from variable</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-smi">$echo</span> <span class="pl-s"><span class="pl-pds">"</span><span class="pl-smi">$long_str</span><span class="pl-pds">"</span></span><span class="pl-k">|</span>grep -q <span class="pl-s"><span class="pl-pds">"</span><span class="pl-smi">$short_str</span><span class="pl-pds">"</span></span>
<span class="pl-k">if</span> [ <span class="pl-smi">$?</span> <span class="pl-k">-eq</span> 0 ]<span class="pl-k">;</span> <span class="pl-k">then</span> <span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">'</span>found<span class="pl-pds">'</span></span><span class="pl-k">;</span> <span class="pl-k">fi</span></pre></div>

<p>//grep -q will output 0 if match found
//remember to add space between []!</p>

<h5>
<a id="grep-strings-between-a-bracket" class="anchor" href="#grep-strings-between-a-bracket" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep strings between a bracket()</h5>

<div class="highlight highlight-source-shell"><pre>grep -oP <span class="pl-s"><span class="pl-pds">'</span>\(\K[^\)]+<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="grep-number-of-characters-with-known-strings-in-betweeneg-aael000001-ra" class="anchor" href="#grep-number-of-characters-with-known-strings-in-betweeneg-aael000001-ra" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>grep number of characters with known strings in between(e.g. AAEL000001-RA)</h5>

<div class="highlight highlight-source-shell"><pre>grep -o -w <span class="pl-s"><span class="pl-pds">"</span>\w\{10\}\-R\w\{1\}<span class="pl-pds">"</span></span></pre></div>

<p>// \w word character [0-9a-zA-Z_] \W not word character </p>

<h5>
<a id="a-lot-examples-here" class="anchor" href="#a-lot-examples-here" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>a lot examples here</h5>

<p><a href="http://www.cyberciti.biz/faq/grep-regular-expressions/">http://www.cyberciti.biz/faq/grep-regular-expressions/</a></p>

<h2>
<a id="sed" class="anchor" href="#sed" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Sed</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="remove-lines-with-word-eg-bbo" class="anchor" href="#remove-lines-with-word-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>remove lines with word (e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">"</span>/bbo/d<span class="pl-pds">"</span></span> filename</pre></div>

<h5>
<a id="edit-infile-edit-and-save" class="anchor" href="#edit-infile-edit-and-save" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>edit infile (edit and save)</h5>

<div class="highlight highlight-source-shell"><pre>sed -i <span class="pl-s"><span class="pl-pds">"</span>/bbo/d<span class="pl-pds">"</span></span> filename</pre></div>

<h5>
<a id="when-using-variable-eg-i-use-double-quotes--" class="anchor" href="#when-using-variable-eg-i-use-double-quotes--" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>when using variable (e.g. $i), use double quotes " "</h5>

<p>e.g. add &gt;$i to the first line (to make a FASTA file)</p>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">"</span>1i &gt;<span class="pl-smi">$i</span><span class="pl-pds">"</span></span>  </pre></div>

<p>//notice the double quotes! in other examples, you can use a single quote, but here, no way! 
//'1i' means insert to first line</p>

<h5>
<a id="delete-empty-lines" class="anchor" href="#delete-empty-lines" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>delete empty lines</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>/^\s*$/d<span class="pl-pds">'</span></span> </pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>s/^$/d<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="delete-last-line" class="anchor" href="#delete-last-line" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>delete last line</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>$d<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="delete-last-character-from-end-of-file" class="anchor" href="#delete-last-character-from-end-of-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>delete last character from end of file</h5>

<div class="highlight highlight-source-shell"><pre>sed -i <span class="pl-s"><span class="pl-pds">'</span>$ s/.$//<span class="pl-pds">'</span></span> filename</pre></div>

<h5>
<a id="add-string-to-end-of-file-eg-" class="anchor" href="#add-string-to-end-of-file-eg-" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add string to end of file (e.g. "]")</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>$s/$/]/<span class="pl-pds">'</span></span> filename</pre></div>

<h5>
<a id="add-string-to-end-of-each-line-eg-" class="anchor" href="#add-string-to-end-of-each-line-eg-" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add string to end of each line (e.g. "}")</h5>

<div class="highlight highlight-source-shell"><pre>sed -e <span class="pl-s"><span class="pl-pds">'</span>s/$/\}\]/<span class="pl-pds">'</span></span> filename</pre></div>

<h5>
<a id="add-n-every-nth-character-eg-every-4th-character" class="anchor" href="#add-n-every-nth-character-eg-every-4th-character" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add \n every nth character (e.g. every 4th character)</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>s/.\{4\}/&amp;\n/g<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="concatenatecombinejoin-files-with-a-seperator-and-next-line-eg-seperate-by-" class="anchor" href="#concatenatecombinejoin-files-with-a-seperator-and-next-line-eg-seperate-by-" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>concatenate/combine/join files with a seperator and next line (e.g seperate by ",")</h5>

<div class="highlight highlight-source-shell"><pre>sed -s <span class="pl-s"><span class="pl-pds">'</span>$a,<span class="pl-pds">'</span></span> <span class="pl-k">*</span>.json <span class="pl-k">&gt;</span> all.json</pre></div>

<h5>
<a id="substitution-eg-replace-a-by-b" class="anchor" href="#substitution-eg-replace-a-by-b" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>substitution (e.g. replace A by B)</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>s/A/B/g<span class="pl-pds">'</span></span> filename </pre></div>

<h5>
<a id="select-lines-start-with-string-eg-bbo" class="anchor" href="#select-lines-start-with-string-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>select lines start with string (e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>sed -n <span class="pl-s"><span class="pl-pds">'</span>/^@S/p<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="delete-lines-with-string-eg-bbo" class="anchor" href="#delete-lines-with-string-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>delete lines with string (e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>/bbo/d<span class="pl-pds">'</span></span> filename </pre></div>

<h5>
<a id="print-every-nth-lines" class="anchor" href="#print-every-nth-lines" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print every nth lines</h5>

<div class="highlight highlight-source-shell"><pre>sed -n <span class="pl-s"><span class="pl-pds">'</span>0~3p<span class="pl-pds">'</span></span> filename</pre></div>

<p>//catch 0: start; 3: step</p>

<h5>
<a id="print-every-odd--lines" class="anchor" href="#print-every-odd--lines" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print every odd # lines</h5>

<div class="highlight highlight-source-shell"><pre>sed -n <span class="pl-s"><span class="pl-pds">'</span>1~2p<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="print-every-third-line-including-the-first-line" class="anchor" href="#print-every-third-line-including-the-first-line" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print every third line including the first line</h5>

<div class="highlight highlight-source-shell"><pre>sed -n <span class="pl-s"><span class="pl-pds">'</span>1p;0~3p<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="remove-leading-whitespace-and-tabs" class="anchor" href="#remove-leading-whitespace-and-tabs" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>remove leading whitespace and tabs</h5>

<div class="highlight highlight-source-shell"><pre>sed -e <span class="pl-s"><span class="pl-pds">'</span>s/^[ \t]*//<span class="pl-pds">'</span></span></pre></div>

<p>//notice a whitespace before '\t'!!</p>

<h5>
<a id="remove-only-leading-whitespace" class="anchor" href="#remove-only-leading-whitespace" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>remove only leading whitespace</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>s/ *//<span class="pl-pds">'</span></span></pre></div>

<p>//notice a whitespace before '*'!!</p>

<h5>
<a id="remove-ending-commas" class="anchor" href="#remove-ending-commas" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>remove ending commas</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>s/,$//g<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="add-a-column-to-the-end" class="anchor" href="#add-a-column-to-the-end" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add a column to the end</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">"</span>s/$/\t<span class="pl-smi">$i</span>/<span class="pl-pds">"</span></span></pre></div>

<p>//$i is the valuable you want to add
e.g. add the filename to every last column of the file</p>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">for</span> <span class="pl-smi">i</span> <span class="pl-k">in</span> <span class="pl-s"><span class="pl-pds">$(</span>ls<span class="pl-pds">)</span></span><span class="pl-k">;</span><span class="pl-k">do</span> sed -i <span class="pl-s"><span class="pl-pds">"</span>s/$/\t<span class="pl-smi">$i</span>/<span class="pl-pds">"</span></span> <span class="pl-smi">$i</span><span class="pl-k">;</span><span class="pl-k">done</span></pre></div>

<h5>
<a id="add-extension-of-filename-to-last-column" class="anchor" href="#add-extension-of-filename-to-last-column" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add extension of filename to last column</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">for</span> <span class="pl-smi">i</span> <span class="pl-k">in</span> T000086_1.02.n T000086_1.02.p<span class="pl-k">;</span><span class="pl-k">do</span> sed <span class="pl-s"><span class="pl-pds">"</span>s/$/\t<span class="pl-smi">${i<span class="pl-k">/*</span>.<span class="pl-k">/</span>}</span>/<span class="pl-pds">"</span></span> <span class="pl-smi">$i</span><span class="pl-k">;</span><span class="pl-k">done</span> <span class="pl-k">&gt;</span>T000086_1.02.np</pre></div>

<h5>
<a id="remove-newline-nextline" class="anchor" href="#remove-newline-nextline" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>remove newline\ nextline</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>:a;N;$!ba;s/\n//g<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="print-a-number-of-lines-eg-line-10th-to-line-33-rd" class="anchor" href="#print-a-number-of-lines-eg-line-10th-to-line-33-rd" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print a number of lines (e.g. line 10th to line 33 rd)</h5>

<div class="highlight highlight-source-shell"><pre>sed -n <span class="pl-s"><span class="pl-pds">'</span>10,33p<span class="pl-pds">'</span></span> <span class="pl-k">&lt;</span>filename</pre></div>

<h5>
<a id="change-delimiter" class="anchor" href="#change-delimiter" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>change delimiter</h5>

<div class="highlight highlight-source-shell"><pre>sed <span class="pl-s"><span class="pl-pds">'</span>s=/=\\/=g<span class="pl-pds">'</span></span></pre></div>

<h1>
<a id="awk" class="anchor" href="#awk" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Awk</h1>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="set-tab-as-field-separator" class="anchor" href="#set-tab-as-field-separator" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>set tab as field separator</h5>

<div class="highlight highlight-source-shell"><pre>awk -F <span class="pl-s"><span class="pl-pds">$'</span><span class="pl-cce">\t</span><span class="pl-pds">'</span></span>  </pre></div>

<h5>
<a id="output-as-tab-separated-also-as-field-separator" class="anchor" href="#output-as-tab-separated-also-as-field-separator" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>output as tab separated (also as field separator)</h5>

<div class="highlight highlight-source-shell"><pre>awk -v OFS=<span class="pl-s"><span class="pl-pds">'</span>\t<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="pass-variable" class="anchor" href="#pass-variable" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>pass variable</h5>

<div class="highlight highlight-source-shell"><pre>a=bbo<span class="pl-k">;</span>b=obb<span class="pl-k">;</span>
awk -v a=<span class="pl-s"><span class="pl-pds">"</span><span class="pl-smi">$a</span><span class="pl-pds">"</span></span> -v b=<span class="pl-s"><span class="pl-pds">"</span><span class="pl-smi">$b</span><span class="pl-pds">"</span></span> <span class="pl-s"><span class="pl-pds">"</span><span class="pl-smi">$1</span>==a &amp;&amp; <span class="pl-smi">$1</span>0=b' filename </span></pre></div>

<h5>
<a id="print-number-of-characters-on-each-line" class="anchor" href="#print-number-of-characters-on-each-line" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print number of characters on each line</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{print length ($0);}<span class="pl-pds">'</span></span> filename </pre></div>

<h5>
<a id="find-number-of-columns" class="anchor" href="#find-number-of-columns" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>find number of columns</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{print NF}<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="reverse-column-order" class="anchor" href="#reverse-column-order" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>reverse column order</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{print $2, $1}<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="check-if-there-is-a-comma-in-a-column-eg-column-1" class="anchor" href="#check-if-there-is-a-comma-in-a-column-eg-column-1" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check if there is a comma in a column (e.g. column $1)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>$1~/,/ {print}<span class="pl-pds">'</span></span>  </pre></div>

<h5>
<a id="split-and-do-for-loop" class="anchor" href="#split-and-do-for-loop" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>split and do for loop</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{split($2, a,",");for (i in a) print $1"\t"a[i]} filename </span></pre></div>

<h5>
<a id="print-all-lines-before-nth-occurence-of-a-string-eg-stop-print-lines-when-bbo-appears-7-times" class="anchor" href="#print-all-lines-before-nth-occurence-of-a-string-eg-stop-print-lines-when-bbo-appears-7-times" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print all lines before nth occurence of a string (e.g stop print lines when bbo appears 7 times)</h5>

<div class="highlight highlight-source-shell"><pre>awk -v N=7 <span class="pl-s"><span class="pl-pds">'</span>{print}/bbo/&amp;&amp; --N&lt;=0 {exit}<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="print-filename-and-last-line-of-all-files-in-directory" class="anchor" href="#print-filename-and-last-line-of-all-files-in-directory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print filename and last line of all files in directory</h5>

<div class="highlight highlight-source-shell"><pre>ls<span class="pl-k">|</span>xargs -n1 -I file awk <span class="pl-s"><span class="pl-pds">'</span>{s=$0};END{print FILENAME,s}<span class="pl-pds">'</span></span> file<span class="pl-s"><span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="add-string-to-the-beginning-of-a-column-eg-add-chr-to-column-3" class="anchor" href="#add-string-to-the-beginning-of-a-column-eg-add-chr-to-column-3" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add string to the beginning of a column (e.g add "chr" to column $3)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>BEGIN{OFS="\t"}$3="chr"$3<span class="pl-pds">'</span></span> </pre></div>

<h5>
<a id="remove-lines-with-string-eg-bbo" class="anchor" href="#remove-lines-with-string-eg-bbo" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>remove lines with string (e.g. bbo)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>!/bbo/<span class="pl-pds">'</span></span> file </pre></div>

<h5>
<a id="column-subtraction" class="anchor" href="#column-subtraction" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>column subtraction</h5>

<div class="highlight highlight-source-shell"><pre>cat file<span class="pl-k">|</span> awk -F <span class="pl-s"><span class="pl-pds">'</span>\t<span class="pl-pds">'</span></span> <span class="pl-s"><span class="pl-pds">'</span>BEGIN {SUM=0}{SUM+=$3-$2}END{print SUM}<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="usage-and-meaning-of-nr-and-fnr" class="anchor" href="#usage-and-meaning-of-nr-and-fnr" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>usage and meaning of NR and FNR</h5>

<p>e.g.
fileA:
a
b
c
fileB:
d
e</p>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>print FILENAME, NR,FNR,$0}<span class="pl-pds">'</span></span> fileA fileB </pre></div>

<p>fileA    1    1    a
fileA    2    2    b
fileA    3    3    c
fileB    4    1    d
fileB    5    2    e</p>

<h5>
<a id="and-gate" class="anchor" href="#and-gate" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>and gate</h5>

<p>e.g.
fileA:
1    0</p>

<p>2    1</p>

<p>3    1</p>

<p>4    0</p>

<p>fileB:</p>

<p>1    0</p>

<p>2    1</p>

<p>3    0</p>

<p>4    1</p>

<div class="highlight highlight-source-shell"><pre>awk -v OFS=<span class="pl-s"><span class="pl-pds">'</span>\t<span class="pl-pds">'</span></span> <span class="pl-s"><span class="pl-pds">'</span>NR=FNR{a[$1]=$2;next} NF {print $1,((a[$1]=$2)? $2:"0")}<span class="pl-pds">'</span></span> fileA fileB </pre></div>

<p>1    0</p>

<p>2    1</p>

<p>3    0</p>

<p>4    0</p>

<h5>
<a id="round-all-numbers-of-file-eg-2-significant-figure" class="anchor" href="#round-all-numbers-of-file-eg-2-significant-figure" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>round all numbers of file (e.g. 2 significant figure)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{while (match($0, /[0-9]+\[0-9]+/)){</span>
<span class="pl-s">    \printf "%s%.2f", substr($0,0,RSTART-1),substr($0,RSTART,RLENGTH)</span>
<span class="pl-s">    \$0=substr($0, RSTART+RLENGTH)</span>
<span class="pl-s">    \}</span>
<span class="pl-s">    \print</span>
<span class="pl-s">    \}<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="give-numberindex-to-every-row" class="anchor" href="#give-numberindex-to-every-row" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>give number/index to every row</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{printf("%s\t%s\n",NR,$0)}<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="break-combine-column-data-into-rows" class="anchor" href="#break-combine-column-data-into-rows" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>break combine column data into rows</h5>

<p>e.g. 
seperate</p>

<p>David    cat,dog</p>

<p>into </p>

<p>David    cat</p>

<p>David    dog</p>

<p>detail here:　<a href="http://stackoverflow.com/questions/33408762/bash-turning-single-comma-separated-column-into-multi-line-string">http://stackoverflow.com/questions/33408762/bash-turning-single-comma-separated-column-into-multi-line-string</a></p>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{split($2,a,",");for(i in a)print $1"\t"a[i]}<span class="pl-pds">'</span></span> file</pre></div>

<h5>
<a id="sum-up-a-file-each-line-in-file-contains-only-one-number" class="anchor" href="#sum-up-a-file-each-line-in-file-contains-only-one-number" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>sum up a file (each line in file contains only one number)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{s+=$1} END {print s}<span class="pl-pds">'</span></span> filename</pre></div>

<h5>
<a id="average-a-file-each-line-in-file-contains-only-one-number" class="anchor" href="#average-a-file-each-line-in-file-contains-only-one-number" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>average a file (each line in file contains only one number)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>{s+=$1}END{print s/NR}<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="print-field-start-with-string-eg-linux" class="anchor" href="#print-field-start-with-string-eg-linux" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print field start with string (e.g Linux)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span>$1 ~ /^Linux/<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="sort-a-row-eg-1-40--35--12--23-----1-12----23--35--40" class="anchor" href="#sort-a-row-eg-1-40--35--12--23-----1-12----23--35--40" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>sort a row (e.g. 1 40  35  12  23  --&gt; 1 12    23  35  40)</h5>

<div class="highlight highlight-source-shell"><pre>awk <span class="pl-s"><span class="pl-pds">'</span> {split( $0, a, "\t" ); asort( a ); for( i = 1; i &lt;= length(a); i++ ) printf( "%s\t", a[i] ); printf( "\n" ); }<span class="pl-pds">'</span></span></pre></div>

<h2>
<a id="xargs" class="anchor" href="#xargs" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Xargs</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="set-tab-as-delimiter-defaultspace" class="anchor" href="#set-tab-as-delimiter-defaultspace" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>set tab as delimiter (default:space)</h5>

<div class="highlight highlight-source-shell"><pre>xargs -d<span class="pl-cce">\t</span></pre></div>

<h5>
<a id="display-3-items-per-line" class="anchor" href="#display-3-items-per-line" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>display 3 items per line</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> 1 2 3 4 5 6<span class="pl-k">|</span> xargs -n 3</pre></div>

<p>//1 2 3
  4 5 6</p>

<h5>
<a id="prompt-before-execution" class="anchor" href="#prompt-before-execution" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>prompt before execution</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> a b c <span class="pl-k">|</span>xargs -p -n 3</pre></div>

<h5>
<a id="print-command-along-with-output" class="anchor" href="#print-command-along-with-output" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print command along with output</h5>

<div class="highlight highlight-source-shell"><pre>xargs -t abcd</pre></div>

<p>///bin/echo abcd
//abcd</p>

<h5>
<a id="with-find-and-rm" class="anchor" href="#with-find-and-rm" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>with find and rm</h5>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> -name <span class="pl-s"><span class="pl-pds">"</span>*.html<span class="pl-pds">"</span></span><span class="pl-k">|</span>xargs rm -rf</pre></div>

<p>delete fiels with whitespace in filename (e.g. "hello 2001")</p>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> -name <span class="pl-s"><span class="pl-pds">"</span>*.c<span class="pl-pds">"</span></span> -print0<span class="pl-k">|</span>xargs -0 rm -rf</pre></div>

<h5>
<a id="show-limits" class="anchor" href="#show-limits" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show limits</h5>

<div class="highlight highlight-source-shell"><pre>xargs --show-limits</pre></div>

<h5>
<a id="move-files-to-folder" class="anchor" href="#move-files-to-folder" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>move files to folder</h5>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> -name <span class="pl-s"><span class="pl-pds">"</span>*.bak<span class="pl-pds">"</span></span> -print 0<span class="pl-k">|</span>xargs -0 -I {} mv {} <span class="pl-k">~</span>/old</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> -name <span class="pl-s"><span class="pl-pds">"</span>*.bak<span class="pl-pds">"</span></span> -print 0<span class="pl-k">|</span>xargs -0 -I file mv file <span class="pl-k">~</span>/old</pre></div>

<h5>
<a id="move-first-100th-files-to-a-directory-eg-d1" class="anchor" href="#move-first-100th-files-to-a-directory-eg-d1" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>move first 100th files to a directory (e.g. d1)</h5>

<div class="highlight highlight-source-shell"><pre>ls <span class="pl-k">|</span>head -100<span class="pl-k">|</span>xargs -I {} mv {} d1</pre></div>

<h5>
<a id="parallel" class="anchor" href="#parallel" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>parallel</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">time</span> <span class="pl-c1">echo</span> {1..5} <span class="pl-k">|</span>xargs -n 1 -P 5 sleep</pre></div>

<p>a lot faster than</p>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">time</span> <span class="pl-c1">echo</span> {1..5} <span class="pl-k">|</span>xargs -n1 sleep</pre></div>

<h5>
<a id="copy-all-files-from-a-to-b" class="anchor" href="#copy-all-files-from-a-to-b" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>copy all files from A to B</h5>

<div class="highlight highlight-source-shell"><pre>find /dir/to/A -type f -name <span class="pl-s"><span class="pl-pds">"</span>*.py<span class="pl-pds">"</span></span> -print 0<span class="pl-k">|</span> xargs -0 -r -I file cp -v -p file --target-directory=/path/to/B</pre></div>

<p>//v: verbose|
//p: keep detail (e.g. owner)</p>

<h5>
<a id="with-sed" class="anchor" href="#with-sed" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>with sed</h5>

<div class="highlight highlight-source-shell"><pre>ls <span class="pl-k">|</span>xargs -n1 -I file sed -i <span class="pl-s"><span class="pl-pds">'</span>/^Pos/d<span class="pl-pds">'</span></span> filename</pre></div>

<h5>
<a id="add-the-file-name-to-the-first-line-of-file" class="anchor" href="#add-the-file-name-to-the-first-line-of-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add the file name to the first line of file</h5>

<div class="highlight highlight-source-shell"><pre>ls <span class="pl-k">|</span>sed <span class="pl-s"><span class="pl-pds">'</span>s/.txt//g<span class="pl-pds">'</span></span><span class="pl-k">|</span>xargs -n1 -I file sed -i -e <span class="pl-s"><span class="pl-pds">'</span>1 i\&gt;file\<span class="pl-pds">'</span></span> file.txt</pre></div>

<h5>
<a id="count-all-files" class="anchor" href="#count-all-files" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>count all files</h5>

<div class="highlight highlight-source-shell"><pre>ls <span class="pl-k">|</span>xargs -n1 wc -l</pre></div>

<h5>
<a id="to-filter-txt-to-a-single-line" class="anchor" href="#to-filter-txt-to-a-single-line" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>to filter txt to a single line</h5>

<div class="highlight highlight-source-shell"><pre>ls -l<span class="pl-k">|</span> xargs</pre></div>

<h5>
<a id="count-files-within-directories" class="anchor" href="#count-files-within-directories" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>count files within directories</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> mso{1..8}<span class="pl-k">|</span>xargs -n1 bash -c <span class="pl-s"><span class="pl-pds">'</span>echo -n "$1:"; ls -la "$1"| grep -w 74 |wc -l<span class="pl-pds">'</span></span> --</pre></div>

<p>// "--" signals the end of options and display further option processing</p>

<h5>
<a id="download-dependencies-files-and-install-eg-requirementstxt" class="anchor" href="#download-dependencies-files-and-install-eg-requirementstxt" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>download dependencies files and install (e.g. requirements.txt)</h5>

<div class="highlight highlight-source-shell"><pre>cat requirements.txt<span class="pl-k">|</span> xargs -n1 sudo pip install</pre></div>

<h5>
<a id="count-lines-in-all-file-also-count-total-lines" class="anchor" href="#count-lines-in-all-file-also-count-total-lines" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>count lines in all file, also count total lines</h5>

<div class="highlight highlight-source-shell"><pre>ls<span class="pl-k">|</span>xargs wc -l</pre></div>

<h2>
<a id="find" class="anchor" href="#find" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Find</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="list-all-sub-directoryfile-in-the-current-directory" class="anchor" href="#list-all-sub-directoryfile-in-the-current-directory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list all sub directory/file in the current directory</h5>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span></pre></div>

<h5>
<a id="list-all-files-under-the-current-directory" class="anchor" href="#list-all-files-under-the-current-directory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list all files under the current directory</h5>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> -type f</pre></div>

<h5>
<a id="list-all-directories-under-the-current-directory" class="anchor" href="#list-all-directories-under-the-current-directory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list all directories under the current directory</h5>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> -type d</pre></div>

<h5>
<a id="edit-all-files-under-current-directory-eg-replace-www-with-ww" class="anchor" href="#edit-all-files-under-current-directory-eg-replace-www-with-ww" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>edit all files under current directory (e.g. replace 'www' with 'ww')</h5>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> name <span class="pl-s"><span class="pl-pds">'</span>*.php<span class="pl-pds">'</span></span> -exec sed -i <span class="pl-s"><span class="pl-pds">'</span>s/www/w/g<span class="pl-pds">'</span></span> {} <span class="pl-cce">\;</span></pre></div>

<p>if no subdirectory</p>

<div class="highlight highlight-source-shell"><pre>replace <span class="pl-s"><span class="pl-pds">"</span>www<span class="pl-pds">"</span></span> <span class="pl-s"><span class="pl-pds">"</span>w<span class="pl-pds">"</span></span> -- <span class="pl-k">*</span></pre></div>

<p>//a space before *</p>

<h5>
<a id="find-and-output-only-filename-eg-mso" class="anchor" href="#find-and-output-only-filename-eg-mso" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>find and output only filename (e.g. "mso")</h5>

<div class="highlight highlight-source-shell"><pre>find mso<span class="pl-k">*</span>/ -name M<span class="pl-k">*</span> -printf <span class="pl-s"><span class="pl-pds">"</span>%f\n<span class="pl-pds">"</span></span></pre></div>

<h5>
<a id="find-and-delete-file-with-size-less-than-eg-74-byte" class="anchor" href="#find-and-delete-file-with-size-less-than-eg-74-byte" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>find and delete file with size less than (e.g. 74 byte)</h5>

<div class="highlight highlight-source-shell"><pre>find <span class="pl-c1">.</span> -name <span class="pl-s"><span class="pl-pds">"</span>*.mso<span class="pl-pds">"</span></span> -size -74c -delete</pre></div>

<p>//M for MB, etc</p>

<h2>
<a id="loops" class="anchor" href="#loops" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Loops</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="while-loop-column-subtraction-of-a-file-eg-a-3-columns-file" class="anchor" href="#while-loop-column-subtraction-of-a-file-eg-a-3-columns-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>while loop, column subtraction of a file (e.g. a 3 columns file)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">while</span> <span class="pl-c1">read</span> a b c<span class="pl-k">;</span> <span class="pl-k">do</span> <span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">$((</span><span class="pl-smi">$c</span><span class="pl-k">-</span><span class="pl-smi">$b</span><span class="pl-pds">))</span></span><span class="pl-k">;</span><span class="pl-k">done</span> <span class="pl-k">&lt;</span> <span class="pl-s"><span class="pl-pds">&lt;(</span>head filename<span class="pl-pds">)</span></span></pre></div>

<p>//there is a space between the two '&lt;'s</p>

<h5>
<a id="while-loop-sum-up-column-subtraction" class="anchor" href="#while-loop-sum-up-column-subtraction" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>while loop, sum up column subtraction</h5>

<div class="highlight highlight-source-shell"><pre>i=0<span class="pl-k">;</span> <span class="pl-k">while</span> <span class="pl-c1">read</span> a b c<span class="pl-k">;</span> <span class="pl-k">do</span> <span class="pl-s"><span class="pl-pds">((</span>i<span class="pl-k">+=</span><span class="pl-smi">$c</span><span class="pl-k">-</span><span class="pl-smi">$b</span><span class="pl-pds">))</span></span><span class="pl-k">;</span> <span class="pl-c1">echo</span> <span class="pl-smi">$i</span><span class="pl-k">;</span> <span class="pl-k">done</span> <span class="pl-k">&lt;</span> <span class="pl-s"><span class="pl-pds">&lt;(</span>head filename<span class="pl-pds">)</span></span></pre></div>

<h5>
<a id="if-loop" class="anchor" href="#if-loop" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>if loop</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">if</span> <span class="pl-s"><span class="pl-pds">((</span><span class="pl-smi">$j</span><span class="pl-k">==</span><span class="pl-smi">$u</span><span class="pl-k">+</span><span class="pl-c1">2</span><span class="pl-pds">))</span></span></pre></div>

<p>//(( )) use for arithmetic operation</p>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">if</span> [[<span class="pl-smi">$age</span> <span class="pl-k">&gt;</span>21]]</pre></div>

<p>//[[ ]] use for comparison</p>

<h5>
<a id="for-loop" class="anchor" href="#for-loop" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>for loop</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">for</span> <span class="pl-smi">i</span> <span class="pl-k">in</span> <span class="pl-s"><span class="pl-pds">$(</span>ls<span class="pl-pds">)</span></span><span class="pl-k">;</span> <span class="pl-k">do</span> <span class="pl-c1">echo</span> file <span class="pl-smi">$i</span><span class="pl-k">;</span><span class="pl-k">done</span></pre></div>

<h2>
<a id="download" class="anchor" href="#download" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Download</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="download-all-from-a-page" class="anchor" href="#download-all-from-a-page" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>download all from a page</h5>

<div class="highlight highlight-source-shell"><pre>wget -r -l1 -H -t1 -nd -N -np -A mp3 -e robots=off http://example.com</pre></div>

<p>//-r: recursive and download all links on page</p>

<p>//-l1: only one level link</p>

<p>//-H: span host, visit other hosts</p>

<p>//-t1: numbers of retries</p>

<p>//-nd: don't make new directories, download to here</p>

<p>//-N: turn on timestamp</p>

<p>//-nd: no parent</p>

<p>//-A: type (seperate by ,)</p>

<p>//-e robots=off: ignore the robots.txt file which stop wget from crashing the site, sorry example.com</p>

<h2>
<a id="random" class="anchor" href="#random" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Random</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="random-pick-100-lines-from-a-file" class="anchor" href="#random-pick-100-lines-from-a-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>random pick 100 lines from a file</h5>

<div class="highlight highlight-source-shell"><pre>shuf -n 100 filename</pre></div>

<h5>
<a id="random-order-lucky-draw" class="anchor" href="#random-order-lucky-draw" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>random order (lucky draw)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">for</span> <span class="pl-smi">i</span> <span class="pl-k">in</span> a b c d e<span class="pl-k">;</span> <span class="pl-k">do</span> <span class="pl-c1">echo</span> <span class="pl-smi">$i</span><span class="pl-k">;</span> <span class="pl-k">done</span><span class="pl-k">|</span> shuf</pre></div>

<h5>
<a id="echo-series-of-random-numbers-between-a-range-eg-generate-15-random-numbers-from-0-10" class="anchor" href="#echo-series-of-random-numbers-between-a-range-eg-generate-15-random-numbers-from-0-10" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>echo series of random numbers between a range (e.g. generate 15 random numbers from 0-10)</h5>

<div class="highlight highlight-source-shell"><pre>shuf -i 0-10 -n 15</pre></div>

<h5>
<a id="echo-a-random-number" class="anchor" href="#echo-a-random-number" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>echo a random number</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> <span class="pl-smi">$RANDOM</span></pre></div>

<h5>
<a id="random-from-0-9" class="anchor" href="#random-from-0-9" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>random from 0-9</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">$((</span>RANDOM <span class="pl-k">%</span> <span class="pl-c1">10</span><span class="pl-pds">))</span></span></pre></div>

<h5>
<a id="random-from-1-10" class="anchor" href="#random-from-1-10" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>random from 1-10</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">$((</span>(RANDOM <span class="pl-k">%</span><span class="pl-c1">10</span>)<span class="pl-k">+</span><span class="pl-c1">1</span><span class="pl-pds">))</span></span></pre></div>

<h2>
<a id="others" class="anchor" href="#others" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Others</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="remove-newline--nextline" class="anchor" href="#remove-newline--nextline" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>remove newline / nextline</h5>

<div class="highlight highlight-source-shell"><pre>tr --delete <span class="pl-s"><span class="pl-pds">'</span>\n<span class="pl-pds">'</span></span> <span class="pl-k">&lt;</span>input.txt <span class="pl-k">&gt;</span>output.txt</pre></div>

<h5>
<a id="replace-newline" class="anchor" href="#replace-newline" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>replace newline</h5>

<div class="highlight highlight-source-shell"><pre>tr <span class="pl-s"><span class="pl-pds">'</span>\n<span class="pl-pds">'</span></span> <span class="pl-s"><span class="pl-pds">'</span> <span class="pl-pds">'</span></span> <span class="pl-k">&lt;</span>filename</pre></div>

<h5>
<a id="compare-files-eg-filea-fileb" class="anchor" href="#compare-files-eg-filea-fileb" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>compare files (e.g. fileA, fileB)</h5>

<div class="highlight highlight-source-shell"><pre>diff fileA fileB</pre></div>

<p>//a: added; d:delete; c:changed</p>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>sdiff fileA fileB</pre></div>

<p>//side-to-side merge of file differences</p>

<h5>
<a id="number-a-file-eg-filea" class="anchor" href="#number-a-file-eg-filea" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>number a file (e.g. fileA)</h5>

<div class="highlight highlight-source-shell"><pre>nl fileA</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>nl -nrz fileA</pre></div>

<p>//add leading zeros</p>

<h5>
<a id="combine-paste-two-files-eg-filea-fileb" class="anchor" href="#combine-paste-two-files-eg-filea-fileb" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>combine/ paste two files (e.g. fileA, fileB)</h5>

<div class="highlight highlight-source-shell"><pre>paste fileA fileB</pre></div>

<p>//default tab seperated</p>

<h5>
<a id="reverse-string" class="anchor" href="#reverse-string" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>reverse string</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> 12345<span class="pl-k">|</span> rev</pre></div>

<h5>
<a id="read-gz-file-without-extracting" class="anchor" href="#read-gz-file-without-extracting" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>read .gz file without extracting</h5>

<div class="highlight highlight-source-shell"><pre>zmore filename</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>zless filename</pre></div>

<h5>
<a id="run-in-background-output-error-file" class="anchor" href="#run-in-background-output-error-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>run in background, output error file</h5>

<div class="highlight highlight-source-shell"><pre>(<span class="pl-c1">command</span> here) <span class="pl-k">2&gt;</span>log <span class="pl-k">&amp;</span></pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>(<span class="pl-c1">command</span> here) <span class="pl-k">2&gt;&amp;1</span><span class="pl-k">|</span> tee logfile</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>(<span class="pl-c1">command</span> here) <span class="pl-k">2&gt;&amp;1</span> <span class="pl-k">&gt;&gt;</span>outfile</pre></div>

<p>//0: standard input; 1: standard output; 2: standard error</p>

<h5>
<a id="send-mail" class="anchor" href="#send-mail" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>send mail</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">'</span>heres the content<span class="pl-pds">'</span></span><span class="pl-k">|</span> mail -A <span class="pl-s"><span class="pl-pds">'</span>file.txt<span class="pl-pds">'</span></span> -s <span class="pl-s"><span class="pl-pds">'</span>mail.subject<span class="pl-pds">'</span></span> me@gmail.com</pre></div>

<p>//use -a flag to set send from (-a "From: <a href="mailto:some@mail.tld">some@mail.tld</a>")</p>

<h5>
<a id="xls-to-csv" class="anchor" href="#xls-to-csv" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>.xls to csv</h5>

<div class="highlight highlight-source-shell"><pre>xls2csv filename</pre></div>

<h5>
<a id="append-to-file-eg-hihi" class="anchor" href="#append-to-file-eg-hihi" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>append to file (e.g. hihi)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">'</span>hihi<span class="pl-pds">'</span></span> <span class="pl-k">&gt;&gt;</span>filename</pre></div>

<h5>
<a id="make-beep-sound" class="anchor" href="#make-beep-sound" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>make BEEP sound</h5>

<div class="highlight highlight-source-shell"><pre>speaker-test -t sine -f 1000 -l1</pre></div>

<h5>
<a id="set-beep-duration" class="anchor" href="#set-beep-duration" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>set beep duration</h5>

<div class="highlight highlight-source-shell"><pre>(speaker-test -t sine -f 1000) <span class="pl-k">&amp;</span> pid=<span class="pl-smi">$!</span><span class="pl-k">;</span>sleep 0.1s<span class="pl-k">;</span><span class="pl-c1">kill</span> -9 <span class="pl-smi">$pid</span></pre></div>

<h5>
<a id="history-edit-delete" class="anchor" href="#history-edit-delete" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>history edit/ delete</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">~</span>/.bash_history</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">history</span> -d [line_number]</pre></div>

<h5>
<a id="get-last-historyrecord-filename" class="anchor" href="#get-last-historyrecord-filename" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>get last history/record filename</h5>

<div class="highlight highlight-source-shell"><pre>head <span class="pl-k">!</span>$</pre></div>

<h5>
<a id="clean-screen" class="anchor" href="#clean-screen" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>clean screen</h5>

<div class="highlight highlight-source-shell"><pre>clear</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>Ctrl+l</pre></div>

<h5>
<a id="send-data-to-last-edited-file" class="anchor" href="#send-data-to-last-edited-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>send data to last edited file</h5>

<div class="highlight highlight-source-shell"><pre>cat /directory/to/file
<span class="pl-c1">echo</span> <span class="pl-k">100&gt;</span><span class="pl-k">!</span>$</pre></div>

<h5>
<a id="run-history-number-eg-53" class="anchor" href="#run-history-number-eg-53" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>run history number (e.g. 53)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">!</span>53</pre></div>

<h5>
<a id="run-last-command" class="anchor" href="#run-last-command" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>run last command</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">!!</span></pre></div>

<h5>
<a id="run-last-command-that-began-with-eg-cat-filename" class="anchor" href="#run-last-command-that-began-with-eg-cat-filename" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>run last command that began with (e.g. cat filename)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">!</span>cat</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">!</span>c</pre></div>

<p>//run cat filename again</p>

<h5>
<a id="extract-xf" class="anchor" href="#extract-xf" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>extract .xf</h5>

<pre><code>1.unxz filename.tar.xz
2.tar -xf filename.tar
</code></pre>

<h5>
<a id="install-python-package" class="anchor" href="#install-python-package" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>install python package</h5>

<div class="highlight highlight-source-shell"><pre>pip install packagename</pre></div>

<h5>
<a id="download-file-if-necessary" class="anchor" href="#download-file-if-necessary" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Download file if necessary</h5>

<div class="highlight highlight-source-shell"><pre>data=file.txt
url=http://www.example.com/<span class="pl-smi">$data</span>
<span class="pl-k">if</span> [<span class="pl-k">!</span> <span class="pl-k">-s</span> <span class="pl-smi">$data</span>]<span class="pl-k">;</span><span class="pl-k">then</span>
    <span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">"</span>downloading test data...<span class="pl-pds">"</span></span>
    wget <span class="pl-smi">$url</span>
<span class="pl-k">fi</span></pre></div>

<h5>
<a id="wget-to-a-filename-when-a-long-name" class="anchor" href="#wget-to-a-filename-when-a-long-name" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>wget to a filename (when a long name)</h5>

<div class="highlight highlight-source-shell"><pre>wget -O filename <span class="pl-s"><span class="pl-pds">"</span>http://example.com<span class="pl-pds">"</span></span></pre></div>

<h5>
<a id="wget-files-to-a-folder" class="anchor" href="#wget-files-to-a-folder" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>wget files to a folder</h5>

<div class="highlight highlight-source-shell"><pre>wget -P /path/to/directory <span class="pl-s"><span class="pl-pds">"</span>http://example.com<span class="pl-pds">"</span></span></pre></div>

<h5>
<a id="delete-current-bash-command" class="anchor" href="#delete-current-bash-command" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>delete current bash command</h5>

<div class="highlight highlight-source-shell"><pre>Ctrl+U</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>Ctrl+C</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>Alt+Shift+#</pre></div>

<p>//to make it to history</p>

<h5>
<a id="add-things-to-history-eg-addmetohistory" class="anchor" href="#add-things-to-history-eg-addmetohistory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add things to history (e.g. "addmetohistory")</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c">#addmetodistory</span></pre></div>

<p>//just add a "#" before~~</p>

<h5>
<a id="sleep-awhile-or-wait-for-a-moment-or-schedule-a-job" class="anchor" href="#sleep-awhile-or-wait-for-a-moment-or-schedule-a-job" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>sleep awhile or wait for a moment or schedule a job</h5>

<div class="highlight highlight-source-shell"><pre>sleep 5<span class="pl-k">;</span><span class="pl-c1">echo</span> hi</pre></div>

<h5>
<a id="count-the-time-for-executing-a-command" class="anchor" href="#count-the-time-for-executing-a-command" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>count the time for executing a command</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">time</span> <span class="pl-c1">echo</span> hi</pre></div>

<h5>
<a id="backup-with-rsync" class="anchor" href="#backup-with-rsync" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>backup with rsync</h5>

<div class="highlight highlight-source-shell"><pre>rsync -av filename filename.bak
rsync -av directory directory.bak
rsync -av --ignore_existing directory/ directory.bak
rsync -av --update directory directory.bak</pre></div>

<p>//skip files that are newer on receiver (i prefer this one!)</p>

<h5>
<a id="make-all-directories-at-one-time" class="anchor" href="#make-all-directories-at-one-time" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>make all directories at one time!</h5>

<div class="highlight highlight-source-shell"><pre>mkdir -p project/{lib/ext,bin,src,doc/{html,info,pdf},demo/stat}</pre></div>

<p>//-p: make parent directory
//this will create project/doc/html/; project/doc/info; project/lib/ext ,etc</p>

<h5>
<a id="run-command-only-if-another-command-returns-zero-exit-status-well-done" class="anchor" href="#run-command-only-if-another-command-returns-zero-exit-status-well-done" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>run command only if another command returns zero exit status (well done)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">cd</span> tmp/ <span class="pl-k">&amp;&amp;</span> tar xvf <span class="pl-k">~</span>/a.tar</pre></div>

<h5>
<a id="run-command-only-if-another-command-returns-non-zero-exit-status-not-finish" class="anchor" href="#run-command-only-if-another-command-returns-non-zero-exit-status-not-finish" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>run command only if another command returns non-zero exit status (not finish)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">cd</span> tmp/a/b/c <span class="pl-k">||</span>mkdir -p tmp/a/b/c</pre></div>

<h5>
<a id="extract-to-a-path" class="anchor" href="#extract-to-a-path" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>extract to a path</h5>

<div class="highlight highlight-source-shell"><pre>tar xvf -C /path/to/directory filename.gz</pre></div>

<h5>
<a id="use-backslash--to-break-long-command" class="anchor" href="#use-backslash--to-break-long-command" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>use backslash "\" to break long command</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">cd</span> tmp/a/b/c \
<span class="pl-k">&gt;</span> <span class="pl-k">||</span> \
<span class="pl-k">&gt;</span>mkdir -p tmp/a/b/c</pre></div>

<h5>
<a id="get-pwd" class="anchor" href="#get-pwd" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>get pwd</h5>

<div class="highlight highlight-source-shell"><pre>VAR=<span class="pl-smi">$PWD</span><span class="pl-k">;</span> <span class="pl-c1">cd</span> <span class="pl-k">~</span><span class="pl-k">;</span> tar xvf -C <span class="pl-smi">$VAR</span> file.tar</pre></div>

<p>//PWD need to be capital letter</p>

<h5>
<a id="list-file-type-of-file-eg-tmp" class="anchor" href="#list-file-type-of-file-eg-tmp" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list file type of file (e.g. /tmp/)</h5>

<div class="highlight highlight-source-shell"><pre>file /tmp/</pre></div>

<p>//tmp/: directory</p>

<h5>
<a id="bash-script" class="anchor" href="#bash-script" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>bash script</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c">#!/bin/bash</span>
file=<span class="pl-smi">${1<span class="pl-k">#*</span>.}</span></pre></div>

<p>//remove string before a "."</p>

<div class="highlight highlight-source-shell"><pre>file=<span class="pl-smi">${1<span class="pl-k">%</span>.<span class="pl-k">*</span>}</span></pre></div>

<p>//remove string after a "."</p>

<h5>
<a id="search-from-history" class="anchor" href="#search-from-history" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>search from history</h5>

<div class="highlight highlight-source-shell"><pre>Ctrl+r</pre></div>

<h5>
<a id="python-simple-http-server" class="anchor" href="#python-simple-http-server" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>python simple HTTP Server</h5>

<div class="highlight highlight-source-shell"><pre>python -m SimpleHTTPServer</pre></div>

<h5>
<a id="variables" class="anchor" href="#variables" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>variables</h5>

<div class="highlight highlight-source-shell"><pre>{i/a/,}</pre></div>

<p>e.g. replace all</p>

<div class="highlight highlight-source-shell"><pre>{i//a/,}</pre></div>

<p>//for variable i, replace all 'a' with a comma</p>

<h5>
<a id="read-user-input" class="anchor" href="#read-user-input" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>read user input</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">read</span> input
<span class="pl-c1">echo</span> <span class="pl-smi">$input</span></pre></div>

<h5>
<a id="generate-sequence-1-10" class="anchor" href="#generate-sequence-1-10" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>generate sequence 1-10</h5>

<div class="highlight highlight-source-shell"><pre>seq 10</pre></div>

<h5>
<a id="sum-up-input-list-eg-seq-10" class="anchor" href="#sum-up-input-list-eg-seq-10" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>sum up input list (e.g. seq 10)</h5>

<div class="highlight highlight-source-shell"><pre>seq 10<span class="pl-k">|</span>paste -sd+<span class="pl-k">|</span>bc</pre></div>

<h5>
<a id="find-average-of-input-listfile" class="anchor" href="#find-average-of-input-listfile" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>find average of input list/file</h5>

<div class="highlight highlight-source-shell"><pre>i=<span class="pl-s"><span class="pl-pds">`</span>wc -l filename<span class="pl-k">|</span>cut -d <span class="pl-s"><span class="pl-pds">'</span> <span class="pl-pds">'</span></span> -f1<span class="pl-pds">`</span></span><span class="pl-k">;</span> cat filename<span class="pl-k">|</span> <span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">"</span>scale=2;(<span class="pl-s"><span class="pl-pds">`</span>paste -sd+<span class="pl-pds">`</span></span>)/<span class="pl-pds">"</span></span><span class="pl-smi">$i</span><span class="pl-k">|</span>bc</pre></div>

<h5>
<a id="generate-all-combination-eg-12" class="anchor" href="#generate-all-combination-eg-12" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>generate all combination (e.g. 1,2)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> {1,2}{1,2}</pre></div>

<p>//1 1, 1 2, 2 1, 2 2</p>

<h5>
<a id="generate-all-combination-eg-atcg" class="anchor" href="#generate-all-combination-eg-atcg" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>generate all combination (e.g. A,T,C,G)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">set</span> = {A,T,C,G}
group= 5
<span class="pl-k">for</span> <span class="pl-s"><span class="pl-pds">((</span>i<span class="pl-k">=</span><span class="pl-c1">0</span>; i<span class="pl-k">&lt;</span><span class="pl-smi">$group</span>; i<span class="pl-k">++</span><span class="pl-pds">))</span></span><span class="pl-k">;</span><span class="pl-k">do</span>
    repetition=<span class="pl-smi">$set$repetition</span><span class="pl-k">;</span><span class="pl-k">done</span>
    bash -c <span class="pl-s"><span class="pl-pds">"</span>echo <span class="pl-pds">"</span></span><span class="pl-smi">$repetition</span><span class="pl-s"><span class="pl-pds">"</span><span class="pl-pds">"</span></span></pre></div>

<h5>
<a id="read-file-content-to-variable" class="anchor" href="#read-file-content-to-variable" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>read file content to variable</h5>

<div class="highlight highlight-source-shell"><pre>foo=<span class="pl-s"><span class="pl-pds">$(</span><span class="pl-k">&lt;</span>test1<span class="pl-pds">)</span></span></pre></div>

<h5>
<a id="echo-size-of-variable" class="anchor" href="#echo-size-of-variable" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>echo size of variable</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> <span class="pl-smi">${<span class="pl-k">#</span>foo}</span></pre></div>

<h5>
<a id="echo-tab" class="anchor" href="#echo-tab" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>echo tab</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">echo</span> -e <span class="pl-s"><span class="pl-pds">'</span> \t <span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="array" class="anchor" href="#array" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>array</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">declare</span> -A array=()</pre></div>

<h5>
<a id="send-a-directory" class="anchor" href="#send-a-directory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>send a directory</h5>

<div class="highlight highlight-source-shell"><pre>scp -r directoryname user@ip:/path/to/send</pre></div>

<h5>
<a id="split-file-into-lines-eg-1000-linessmallfile" class="anchor" href="#split-file-into-lines-eg-1000-linessmallfile" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>split file into lines (e.g. 1000 lines/smallfile)</h5>

<div class="highlight highlight-source-shell"><pre>$ split -d -l 1000 bigfilename</pre></div>

<h2>
<a id="system" class="anchor" href="#system" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>System</h2>

<p>[<a href="#handy-bash-oneliner-commands-for-tsv-file-editing">back to top</a>]</p>

<h5>
<a id="snapshot-of-the-current-processes" class="anchor" href="#snapshot-of-the-current-processes" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>snapshot of the current processes</h5>

<div class="highlight highlight-source-shell"><pre>ps </pre></div>

<h5>
<a id="check-graphics-card" class="anchor" href="#check-graphics-card" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check graphics card</h5>

<div class="highlight highlight-source-shell"><pre>lspci</pre></div>

<h5>
<a id="show-ip-address" class="anchor" href="#show-ip-address" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show IP address</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-smi">$ip</span> add show</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>ifconfig</pre></div>

<h5>
<a id="check-system-version" class="anchor" href="#check-system-version" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check system version</h5>

<div class="highlight highlight-source-shell"><pre>cat /etc/<span class="pl-k">*</span>-release</pre></div>

<h5>
<a id="linux-programmers-manuel-hier--description-of-the-filesystem-hierarchy" class="anchor" href="#linux-programmers-manuel-hier--description-of-the-filesystem-hierarchy" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>Linux Programmer's Manuel: hier- description of the filesystem hierarchy</h5>

<div class="highlight highlight-source-shell"><pre>man hier</pre></div>

<h5>
<a id="list-job" class="anchor" href="#list-job" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list job</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">jobs</span> -l</pre></div>

<h5>
<a id="export-path" class="anchor" href="#export-path" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>export PATH</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">export</span> PATH=<span class="pl-smi">$PATH</span>:<span class="pl-k">~</span>/path/you/want</pre></div>

<h5>
<a id="make-file-execuable" class="anchor" href="#make-file-execuable" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>make file execuable</h5>

<div class="highlight highlight-source-shell"><pre>chmod +x filename</pre></div>

<p>//you can now ./filename to execute it</p>

<h5>
<a id="list-screen" class="anchor" href="#list-screen" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list screen</h5>

<div class="highlight highlight-source-shell"><pre>screen -d -r</pre></div>

<h5>
<a id="echo-screen-name" class="anchor" href="#echo-screen-name" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>echo screen name</h5>

<div class="highlight highlight-source-shell"><pre>screen -ls</pre></div>

<h5>
<a id="check-system-x86-64" class="anchor" href="#check-system-x86-64" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check system (x86-64)</h5>

<div class="highlight highlight-source-shell"><pre>uname -i</pre></div>

<h5>
<a id="surf-the-net" class="anchor" href="#surf-the-net" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>surf the net</h5>

<div class="highlight highlight-source-shell"><pre>links www.google.com</pre></div>

<h5>
<a id="add-user-set-passwd" class="anchor" href="#add-user-set-passwd" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>add user, set passwd</h5>

<div class="highlight highlight-source-shell"><pre>useradd username
passwd username</pre></div>

<h5>
<a id="edit-variable-for-bash-eg-displaying-the-whole-path" class="anchor" href="#edit-variable-for-bash-eg-displaying-the-whole-path" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>edit variable for bash, (e.g. displaying the whole path)</h5>

<div class="highlight highlight-source-shell"><pre>1. joe <span class="pl-k">~</span>/.bash_profile 
2. <span class="pl-k">export</span> PS1=<span class="pl-s"><span class="pl-pds">'</span>\u@\h:\w\$<span class="pl-pds">'</span></span> </pre></div>

<p>//$PS1 is a variable that defines the makeup and style of the command prompt </p>

<div class="highlight highlight-source-shell"><pre>3. <span class="pl-c1">source</span> <span class="pl-k">~</span>/.bash_profile</pre></div>

<h5>
<a id="edit-environment-setting-eg-alias" class="anchor" href="#edit-environment-setting-eg-alias" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>edit environment setting (e.g. alias)</h5>

<div class="highlight highlight-source-shell"><pre>1. joe <span class="pl-k">~</span>/.bash_profile
2. <span class="pl-c1">alias</span> pd=<span class="pl-s"><span class="pl-pds">"</span>pwd<span class="pl-pds">"</span></span> //no more need to <span class="pl-c1">type</span> that <span class="pl-s"><span class="pl-pds">'</span>w<span class="pl-pds">'</span></span><span class="pl-k">!</span>
3. <span class="pl-c1">source</span> <span class="pl-k">~</span>/.bash_profile</pre></div>

<h5>
<a id="list-environment-variables-eg-path" class="anchor" href="#list-environment-variables-eg-path" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list environment variables (e.g. PATH)</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-smi">$echo</span> <span class="pl-smi">$PATH</span></pre></div>

<p>//list of directories separated by a colon</p>

<h5>
<a id="list-all-environment-variables-for-current-user" class="anchor" href="#list-all-environment-variables-for-current-user" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list all environment variables for current user</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-smi">$env</span></pre></div>

<h5>
<a id="show-partition-format" class="anchor" href="#show-partition-format" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show partition format</h5>

<div class="highlight highlight-source-shell"><pre>lsblk</pre></div>

<h5>
<a id="soft-link-program-to-bin" class="anchor" href="#soft-link-program-to-bin" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>soft link program to bin</h5>

<div class="highlight highlight-source-shell"><pre>ln -s /path/to/program /home/usr/bin</pre></div>

<p>//must be the whole path to the program</p>

<h5>
<a id="show-hexadecimal-view-of-data" class="anchor" href="#show-hexadecimal-view-of-data" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show hexadecimal view of data</h5>

<div class="highlight highlight-source-shell"><pre>hexdump -C filename.class</pre></div>

<h5>
<a id="jump-to-different-node" class="anchor" href="#jump-to-different-node" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>jump to different node</h5>

<div class="highlight highlight-source-shell"><pre>rsh node_name</pre></div>

<h5>
<a id="check-port-active-internet-connection" class="anchor" href="#check-port-active-internet-connection" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check port (active internet connection)</h5>

<div class="highlight highlight-source-shell"><pre>netstat -tulpn</pre></div>

<h5>
<a id="find-whick-link-to-a-file" class="anchor" href="#find-whick-link-to-a-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>find whick link to a file</h5>

<div class="highlight highlight-source-shell"><pre>readlink filename</pre></div>

<h5>
<a id="check-where-a-command-link-to-eg-python" class="anchor" href="#check-where-a-command-link-to-eg-python" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check where a command link to (e.g. python)</h5>

<div class="highlight highlight-source-shell"><pre>which python</pre></div>

<h5>
<a id="list-total-size-of-a-directory" class="anchor" href="#list-total-size-of-a-directory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list total size of a directory</h5>

<div class="highlight highlight-source-shell"><pre>du -hs <span class="pl-c1">.</span></pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>du -sb</pre></div>

<h5>
<a id="copy-directory-with-permission-setting" class="anchor" href="#copy-directory-with-permission-setting" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>copy directory with permission setting</h5>

<div class="highlight highlight-source-shell"><pre>cp -rp /path/to/directory</pre></div>

<h5>
<a id="store-current-directory" class="anchor" href="#store-current-directory" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>store current directory</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">pushd</span> <span class="pl-c1">.</span> <span class="pl-smi">$popd</span> <span class="pl-k">;</span><span class="pl-c1">dirs</span> -l </pre></div>

<h5>
<a id="show-disk-usage" class="anchor" href="#show-disk-usage" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show disk usage</h5>

<div class="highlight highlight-source-shell"><pre>df -h </pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>du -h </pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>du -sk /var/log/<span class="pl-k">*</span> <span class="pl-k">|</span>sort -rn <span class="pl-k">|</span>head -10</pre></div>

<h5>
<a id="show-current-runlevel" class="anchor" href="#show-current-runlevel" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show current runlevel</h5>

<div class="highlight highlight-source-shell"><pre>runlevel</pre></div>

<h5>
<a id="switch-runlevel" class="anchor" href="#switch-runlevel" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>switch runlevel</h5>

<div class="highlight highlight-source-shell"><pre>init 3 </pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>telinit 3 </pre></div>

<h5>
<a id="permanently-modify-runlevel" class="anchor" href="#permanently-modify-runlevel" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>permanently modify runlevel</h5>

<div class="highlight highlight-source-shell"><pre>1. edit /etc/init/rc-sysinit.conf 
2. env DEFAULT_RUNLEVEL=2 </pre></div>

<h5>
<a id="become-root" class="anchor" href="#become-root" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>become root</h5>

<div class="highlight highlight-source-shell"><pre>su</pre></div>

<h5>
<a id="become-somebody" class="anchor" href="#become-somebody" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>become somebody</h5>

<div class="highlight highlight-source-shell"><pre>su somebody</pre></div>

<h5>
<a id="report-user-quotes-on-device" class="anchor" href="#report-user-quotes-on-device" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>report user quotes on device</h5>

<div class="highlight highlight-source-shell"><pre>requota -auvs</pre></div>

<h5>
<a id="get-entries-in-a-number-of-important-databases" class="anchor" href="#get-entries-in-a-number-of-important-databases" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>get entries in a number of important databases</h5>

<div class="highlight highlight-source-shell"><pre>getent database_name</pre></div>

<p>(e.g. the 'passwd' database)</p>

<div class="highlight highlight-source-shell"><pre>getent passwd</pre></div>

<p>//list all user account (all local and LDAP)
(e.g. fetch list of grop accounts)</p>

<div class="highlight highlight-source-shell"><pre>getent group</pre></div>

<p>//store in database 'group'</p>

<h5>
<a id="little-xwindow-tools" class="anchor" href="#little-xwindow-tools" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>little xwindow tools</h5>

<div class="highlight highlight-source-shell"><pre>xclock
xeyes</pre></div>

<h5>
<a id="change-owner-of-file" class="anchor" href="#change-owner-of-file" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>change owner of file</h5>

<div class="highlight highlight-source-shell"><pre>chown user_name filename
chown -R user_name /path/to/directory/</pre></div>

<p>//chown user:group filename</p>

<h5>
<a id="list-current-mount-detail" class="anchor" href="#list-current-mount-detail" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list current mount detail</h5>

<div class="highlight highlight-source-shell"><pre>df</pre></div>

<h5>
<a id="list-current-usernames-and-user-numbers" class="anchor" href="#list-current-usernames-and-user-numbers" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>list current usernames and user-numbers</h5>

<div class="highlight highlight-source-shell"><pre>cat /etc/passwd</pre></div>

<h5>
<a id="get-all-username" class="anchor" href="#get-all-username" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>get all username</h5>

<div class="highlight highlight-source-shell"><pre>getent passwd<span class="pl-k">|</span> awk <span class="pl-s"><span class="pl-pds">'</span>{FS="[:]"; print $1}<span class="pl-pds">'</span></span></pre></div>

<h5>
<a id="show-all-users" class="anchor" href="#show-all-users" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show all users</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">compgen</span> -u</pre></div>

<h5>
<a id="show-all-groups" class="anchor" href="#show-all-groups" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show all groups</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">compgen</span> -g</pre></div>

<h5>
<a id="show-group-of-user" class="anchor" href="#show-group-of-user" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show group of user</h5>

<div class="highlight highlight-source-shell"><pre>group username</pre></div>

<h5>
<a id="show-uid-gid-group-of-user" class="anchor" href="#show-uid-gid-group-of-user" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show uid, gid, group of user</h5>

<div class="highlight highlight-source-shell"><pre>id username</pre></div>

<h5>
<a id="check-if-its-root" class="anchor" href="#check-if-its-root" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check if it's root</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">if</span> [<span class="pl-s"><span class="pl-pds">$(</span>id -u<span class="pl-pds">)</span></span> <span class="pl-k">-ne</span> 0]<span class="pl-k">;</span><span class="pl-k">then</span>
    <span class="pl-c1">echo</span> <span class="pl-s"><span class="pl-pds">"</span>You are not root!<span class="pl-pds">"</span></span>
    <span class="pl-c1">exit</span><span class="pl-k">;</span>
<span class="pl-k">fi</span></pre></div>

<p>//'id -u' output 0 if it's not root</p>

<h5>
<a id="find-out-cpu-information" class="anchor" href="#find-out-cpu-information" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>find out CPU information</h5>

<div class="highlight highlight-source-shell"><pre>more /proc/cpuinfo</pre></div>

<p>or</p>

<div class="highlight highlight-source-shell"><pre>lscpu</pre></div>

<h5>
<a id="set-quota-for-user-eg-disk-soft-limit-120586240-hard-limit-125829120" class="anchor" href="#set-quota-for-user-eg-disk-soft-limit-120586240-hard-limit-125829120" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>set quota for user (e.g. disk soft limit: 120586240; hard limit: 125829120)</h5>

<div class="highlight highlight-source-shell"><pre>setquota username 120586240 125829120 0 0 /home</pre></div>

<h5>
<a id="show-quota-for-user" class="anchor" href="#show-quota-for-user" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show quota for user</h5>

<div class="highlight highlight-source-shell"><pre>quota -v username</pre></div>

<h5>
<a id="fork-bomb" class="anchor" href="#fork-bomb" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>fork bomb</h5>

<div class="highlight highlight-source-shell"><pre>:(){:<span class="pl-k">|</span>:<span class="pl-k">&amp;</span>}<span class="pl-k">;</span>:</pre></div>

<p>//dont try this at home</p>

<h5>
<a id="check-user-login" class="anchor" href="#check-user-login" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check user login</h5>

<div class="highlight highlight-source-shell"><pre>lastlog</pre></div>

<h5>
<a id="edit-path-for-all-users" class="anchor" href="#edit-path-for-all-users" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>edit path for all users</h5>

<div class="highlight highlight-source-shell"><pre>joe /etc/environment</pre></div>

<p>//edit this file</p>

<h5>
<a id="show-running-processes" class="anchor" href="#show-running-processes" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show running processes</h5>

<div class="highlight highlight-source-shell"><pre>ps aux</pre></div>

<h5>
<a id="find-maximum-number-of-processes" class="anchor" href="#find-maximum-number-of-processes" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>find maximum number of processes</h5>

<div class="highlight highlight-source-shell"><pre>cat /proc/sys/kernal/pid_max</pre></div>

<h5>
<a id="show-and-set-user-limit" class="anchor" href="#show-and-set-user-limit" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>show and set user limit</h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-c1">ulimit</span> -u</pre></div>

<h5>
<a id="which-ports-are-listening-for-tcp-connections-from-the-network" class="anchor" href="#which-ports-are-listening-for-tcp-connections-from-the-network" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>which ports are listening for TCP connections from the network</h5>

<div class="highlight highlight-source-shell"><pre>nmap -sT -O localhost</pre></div>

<h5>
<a id="print-out-number-of-cores-processors" class="anchor" href="#print-out-number-of-cores-processors" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>print out number of cores/ processors</h5>

<div class="highlight highlight-source-shell"><pre>nproc --all</pre></div>

<h5>
<a id="check-status-of-each-core" class="anchor" href="#check-status-of-each-core" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>check status of each core</h5>

<ol>
<li>top</li>
<li>press '1'</li>
</ol>

<p>=-=-=-=-=-A lot more coming!! =-=-=-=-=-=-=-=-=-=waitwait-=-=-=-=-=-=-=-=-=-</p>
  
  </body>
</html>
