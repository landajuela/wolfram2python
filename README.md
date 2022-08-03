# Wolfram ↔ Python
## general
---
 Name | Wolfram | Python
:---:|:---|:---
func|<pre>f[x_]:=2 + x;f[2]</pre>|<pre>def f(x):<br/>    return 2 + x<br/>f(2)<br/></pre>
global|<pre>Names["Global`*"]</pre>|<pre>globals()</pre>
print|<pre>Print["Hello world"]</pre>|<pre>print("Hello world")</pre>
range|<pre>Range[0,7,2]</pre>|<pre>range(0,7,2)</pre>


## dict
---
 Name | Wolfram | Python
:---:|:---|:---
dict|<pre><\|"a" -> 2, "b" -> 2, "c" -> 6, "d" -> 7\|></pre>|<pre>{"a": 2, "b": 2, "c": 6, "d": 7}</pre>
dict access|<pre><\|"a" -> 2, "b" -> 2, "c" -> 6, "d" -> 7\|>["a"]</pre>|<pre>{"a": 2, "b": 2, "c": 6, "d": 7}["a"]</pre>


## functional programming
---
 Name | Wolfram | Python
:---:|:---|:---
func nest|<pre>NestList[f[#]&,2,3]</pre>|<pre>def nest(f, x, times):<br/>    y = [x]<br/>    for i in range(times-1):<br/>        y.append(f(y[-1]))<br/>    return y<br/>nest(f,2,3)<br/></pre>
map|<pre>Function[x,2 + x]/@{2, 2, 6, 7}</pre>|<pre>map(lambda x : 2 + x, [2, 2, 6, 7])</pre>


## list
---
 Name | Wolfram | Python
:---:|:---|:---
list|<pre>{2, 2, 6, 7}</pre>|<pre>[2, 2, 6, 7]</pre>
list append|<pre>l={2, 2, 6, 7}; AppendTo[l,2]; l</pre>|<pre>l=[2, 2, 6, 7]; l.append(2); l</pre>
list length|<pre>Length[{2, 2, 6, 7}]</pre>|<pre>len([2, 2, 6, 7])</pre>
list slicing|<pre>{2, 2, 6, 7}[[1;;;;2]]</pre>|<pre>[2, 2, 6, 7][0::2]</pre>
list zip|<pre>Transpose@{{"a", "b", "c", "d"},{2, 2, 6, 7}}</pre>|<pre>list(zip(["a", "b", "c", "d"],[2, 2, 6, 7]))</pre>
unique list|<pre>DeleteDuplicates[{2, 2, 6, 7}]</pre>|<pre>set([2, 2, 6, 7])</pre>


## procedural programming
---
 Name | Wolfram | Python
:---:|:---|:---
if|<pre>If[3>2,Print["true"]]</pre>|<pre>if 3 > 2:<br/>    print("true")<br/></pre>


## string
---
 Name | Wolfram | Python
:---:|:---|:---
string format|<pre>ToString[StringForm["The values are x=`` and y=``.", 5, 10]]</pre>|<pre>"The values are x={} and y={}.".format(5, 10)</pre>
string join|<pre>StringRiffle[{2, 2, 6, 7}, " "]</pre>|<pre>' '.join(["2", "2", "6", "7"])</pre>


