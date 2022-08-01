# Wolfram ↔ Python
## general
---
 Name | Wolfram | Python
:---:|:---|:---
func|<pre><code>f[x_]:=2 + x;f[2]</code></pre>|<pre><code>def f(x):<br>	return 2 + x<br>f(2)<br></code></pre>
global|<pre><code>Names["Global`*"]</code></pre>|<pre><code>globals()</code></pre>
print|<pre><code>Print["Hello world"]</code></pre>|<pre><code>print("Hello world")</code></pre>
range|<pre><code>Range[0,7,2]</code></pre>|<pre><code>range(0,7,2)</code></pre>


## dict
---
 Name | Wolfram | Python
:---:|:---|:---
dict|<pre><code><\|"a" -> 2, "b" -> 2, "c" -> 6\|></code></pre>|<pre><code>{"a": 2, "b": 2, "c": 6}</code></pre>
dict access|<pre><code><\|"a" -> 2, "b" -> 2, "c" -> 6\|>["a"]</code></pre>|<pre><code>{"a": 2, "b": 2, "c": 6}["a"]</code></pre>


## functional programming
---
 Name | Wolfram | Python
:---:|:---|:---
func nest|<pre><code>NestList[f[#]&,2,3]</code></pre>|<pre><code>def nest(f, x, times):<br>    y = [x]<br>    for i in range(times-1):<br>        y.append(f(y[-1]))<br>    return y<br>nest(f,2,3)<br></code></pre>
map|<pre><code>Function[x,2 + x]/@{2, 2, 6}</code></pre>|<pre><code>map(lambda x : 2 + x, [2, 2, 6])</code></pre>


## list
---
 Name | Wolfram | Python
:---:|:---|:---
list|<pre><code>{2, 2, 6}</code></pre>|<pre><code>[2, 2, 6]</code></pre>
list append|<pre><code>l={2, 2, 6}; AppendTo[l,2]; l</code></pre>|<pre><code>l=[2, 2, 6]; l.append(2); l</code></pre>
list length|<pre><code>Length[{2, 2, 6}]</code></pre>|<pre><code>len([2, 2, 6])</code></pre>
list slicing|<pre><code>{2, 2, 6}[[1;;;;2]]</code></pre>|<pre><code>[2, 2, 6][0::2]</code></pre>
list zip|<pre><code>Transpose@{{"a", "b", "c"},{2, 2, 6}}</code></pre>|<pre><code>list(zip(["a", "b", "c"],[2, 2, 6]))</code></pre>
unique list|<pre><code>DeleteDuplicates[{2, 2, 6}]</code></pre>|<pre><code>set([2, 2, 6])</code></pre>


## procedural programming
---
 Name | Wolfram | Python
:---:|:---|:---
if|<pre><code>If[3>2,Print["true"]]</code></pre>|<pre><code>if 3 > 2:<br>	print("true")<br></code></pre>


## string
---
 Name | Wolfram | Python
:---:|:---|:---
string format|<pre><code>StringForm["The values are x=`` and y=``.", 5, 10]</code></pre>|<pre><code>"The values are x={} and y={}.".format(5, 10)</code></pre>
string join|<pre><code>StringRiffle[{2, 2, 6}, " "]</code></pre>|<pre><code>' '.join(["2", "2", "6"])</code></pre>


