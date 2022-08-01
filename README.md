# Wolfram ↔ Python
## general
---
 Name | Wolfram | Python
:---:|:---|:---
func|<code>f[x_]:=2 + x;f[2]</code>|<code>def f(x):<br>	return 2 + x<br>f(2)<br></code>
global|<code>Names["Global`*"]</code>|<code>globals()</code>
print|<code>Print["Hello world"]</code>|<code>print("Hello world")</code>
range|<code>Range[0,7,2]</code>|<code>range(0,7,2)</code>


## dict
---
 Name | Wolfram | Python
:---:|:---|:---
dict|<code><\|"a" -> 2, "b" -> 2, "c" -> 6\|></code>|<code>{"a": 2, "b": 2, "c": 6}</code>
dict access|<code><\|"a" -> 2, "b" -> 2, "c" -> 6\|>["a"]</code>|<code>{"a": 2, "b": 2, "c": 6}["a"]</code>


## functional programming
---
 Name | Wolfram | Python
:---:|:---|:---
func nest|<code>NestList[f[#]&,2,3]</code>|<code>def nest(f, x, times):<br>    y = [x]<br>    for i in range(times-1):<br>        y.append(f(y[-1]))<br>    return y<br>nest(f,2,3)<br></code>
map|<code>Function[x,2 + x]/@{2, 2, 6}</code>|<code>map(lambda x : 2 + x, [2, 2, 6])</code>


## list
---
 Name | Wolfram | Python
:---:|:---|:---
list|<code>{2, 2, 6}</code>|<code>[2, 2, 6]</code>
list append|<code>l={2, 2, 6}; AppendTo[l,2]; l</code>|<code>l=[2, 2, 6]; l.append(2); l</code>
list length|<code>Length[{2, 2, 6}]</code>|<code>len([2, 2, 6])</code>
list slicing|<code>{2, 2, 6}[[1;;;;2]]</code>|<code>[2, 2, 6][0::2]</code>
list zip|<code>Transpose@{{"a", "b", "c"},{2, 2, 6}}</code>|<code>list(zip(["a", "b", "c"],[2, 2, 6]))</code>
unique list|<code>DeleteDuplicates[{2, 2, 6}]</code>|<code>set([2, 2, 6])</code>


## procedural programming
---
 Name | Wolfram | Python
:---:|:---|:---
if|<code>If[3>2,Print["true"]]</code>|<code>if 3 > 2:<br>	print("true")<br></code>


## string
---
 Name | Wolfram | Python
:---:|:---|:---
string format|<code>StringForm["The values are x=`` and y=``.", 5, 10]</code>|<code>"The values are x={} and y={}.".format(5, 10)</code>
string join|<code>StringRiffle[{2, 2, 6}, " "]</code>|<code>' '.join(["2", "2", "6"])</code>


