# Wolfram ↔ Python

Welcome to **Wolfram ↔ Python**, a quick reference guide that mirrors common Wolfram Language constructs with their closest Python equivalents. Whether you’re coming from Mathematica and want to prototype logic in Python, or you’re a Pythonista looking to explore Wolfram’s powerful symbolic and functional paradigms, this cheat-sheet will help you translate ideas between the two ecosystems at a glance. Each section groups related operations—everything from basic functions and data structures to functional and procedural programming patterns—so you can jump straight to what you need. Enjoy seamless code translation and unleash the strengths of both languages!

## general

 Name | Wolfram | Python
:---:|:---|:---
anonymous function|<pre>#^2&/@{2, 2, 9, 6, 7}</pre>|<pre>[x**2 for x in [2, 2, 9, 6, 7]]</pre>
func|<pre>f[x_]:=2 + x;f[2]</pre>|<pre>def f(x):<br/>    return 2 + x<br/>f(2)<br/></pre>
global|<pre>Names["Global`*"]</pre>|<pre>globals()</pre>
print|<pre>Print["Hello world"]</pre>|<pre>print("Hello world")</pre>
range|<pre>Range[0,7,2]</pre>|<pre>range(0,7,2)</pre>

## dict

 Name | Wolfram | Python
:---:|:---|:---
add or update key|<pre>assoc = <\|"a" -> 1\|>; assoc["b"] = 2; assoc</pre>|<pre>d = {"a": 1}; d["b"] = 2; d</pre>
dict|<pre><\|"a" -> 2, "b" -> 2, "c" -> 9, "d" -> 6, "e" -> 7\|></pre>|<pre>{"a": 2, "b": 2, "c": 9, "d": 6, "e": 7}</pre>
dict access|<pre><\|"a" -> 2, "b" -> 2, "c" -> 9, "d" -> 6, "e" -> 7\|>["a"]</pre>|<pre>{"a": 2, "b": 2, "c": 9, "d": 6, "e": 7}["a"]</pre>
keys list|<pre>Keys[<\|"a"->1, "b"->2\|>]</pre>|<pre>d = {"a": 1, "b": 2}; d.keys()</pre>
remove key|<pre>KeyDrop[<\|"a" -> 1, "b" -> 2\|>, "a"]</pre>|<pre>d = {"a": 1, "b": 2}; del d["a"]; d</pre>
values list|<pre>Values[<\|"a"->1, "b"->2\|>]</pre>|<pre>d = {"a": 1, "b": 2}; d.values()</pre>

## functional programming

 Name | Wolfram | Python
:---:|:---|:---
Anonymous pure function|<pre>(#1 + #2)&[2,3]</pre>|<pre>(lambda a,b: a + b)(2,3)</pre>
Fold (reduce)|<pre>Fold[Plus, 0, {1,2,3,4}]</pre>|<pre>from functools import reduce<br/>reduce(lambda a,b: a+b, [1,2,3,4], 0)<br/></pre>
func nest|<pre>NestList[f[#]&,2,3]</pre>|<pre>def nest(f, x, times):<br/>    y = [x]<br/>    for i in range(times-1):<br/>        y.append(f(y[-1]))<br/>    return y<br/>nest(f,2,3)<br/></pre>
map|<pre>Function[x,2 + x]/@{2, 2, 9, 6, 7}</pre>|<pre>map(lambda x : 2 + x, [2, 2, 9, 6, 7])</pre>
Partition / chunk|<pre>Partition[{1,2,3,4,5,6}, 2]</pre>|<pre>lst = [1,2,3,4,5,6]<br/>[lst[i:i+2] for i in range(0, len(lst), 2)]<br/></pre>
Select / filter|<pre>Select[{1,2,3,4}, EvenQ]</pre>|<pre>filter(lambda x: x % 2 == 0, [1,2,3,4])</pre>

## list

 Name | Wolfram | Python
:---:|:---|:---
element position|<pre>Position[{a,b,c}, b][[1,1]]-1</pre>|<pre>[i for i,v in enumerate(['a','b','c']) if v == 'b'][0]</pre>
flatten nested|<pre>Flatten[{{1,2},{3,4}}]</pre>|<pre>import itertools<br/>list(itertools.chain.from_iterable([[1,2],[3,4]]))<br/></pre>
list|<pre>{2, 2, 9, 6, 7}</pre>|<pre>[2, 2, 9, 6, 7]</pre>
list append|<pre>l={2, 2, 9, 6, 7}; AppendTo[l,2]; l</pre>|<pre>l=[2, 2, 9, 6, 7]; l.append(2); l</pre>
list length|<pre>Length[{2, 2, 9, 6, 7}]</pre>|<pre>len([2, 2, 9, 6, 7])</pre>
list slicing|<pre>{2, 2, 9, 6, 7}[[1;;-1;;2]]</pre>|<pre>[2, 2, 9, 6, 7][0::2]</pre>
list zip|<pre>Transpose@{{"a", "b", "c", "d", "e"},{2, 2, 9, 6, 7}}</pre>|<pre>list(zip(["a", "b", "c", "d", "e"],[2, 2, 9, 6, 7]))</pre>
random sample|<pre>RandomSample[{1,2,3,4}, 2]</pre>|<pre>import random;random.sample([1,2,3,4], 2)</pre>
reverse list|<pre>Reverse[{1,2,3}]</pre>|<pre>list(reversed([1,2,3]))</pre>
sort|<pre>Sort[{2, 2, 9, 6, 7}]</pre>|<pre>sorted([2, 2, 9, 6, 7])</pre>
unique list|<pre>DeleteDuplicates[{2, 2, 9, 6, 7}]</pre>|<pre>set([2, 2, 9, 6, 7])</pre>

## math

 Name | Wolfram | Python
:---:|:---|:---
factorial|<pre>Factorial[7]</pre>|<pre>import math; math.factorial(7)</pre>
square root|<pre>Sqrt[9]</pre>|<pre>import math; math.sqrt(9)</pre>

## procedural programming

 Name | Wolfram | Python
:---:|:---|:---
break/exit loop|<pre>For[i = 1, i < 10, i++, If[i > 5, Break[]]]</pre>|<pre>for i in range(1,10):<br/>    if i > 5: break<br/></pre>
for loop|<pre>Do[Print[i], {i, 1, 5}]</pre>|<pre>for i in range(1,6):<br/>    print(i)<br/></pre>
if|<pre>If[3>2,Print["true"]]</pre>|<pre>if 3 > 2:<br/>    print("true")<br/></pre>
while loop|<pre>i = 0; While[i < 5, i++; Print[i]]</pre>|<pre>i = 0<br/>while i < 5:<br/>    i += 1<br/>    print(i)<br/></pre>

## string

 Name | Wolfram | Python
:---:|:---|:---
replace substring|<pre>StringReplace["a_b_c", "_"->"-"]</pre>|<pre>"a_b_c".replace("_","-")</pre>
string format|<pre>ToString[StringForm["The values are x=`` and y=``.", 5, 10]]</pre>|<pre>"The values are x={} and y={}.".format(5, 10)</pre>
string join|<pre>StringRiffle[{2, 2, 9, 6, 7}, " "]</pre>|<pre>' '.join(["2", "2", "9", "6", "7"])</pre>
string length|<pre>StringLength["hello"]</pre>|<pre>len("hello")</pre>
substring|<pre>StringTake["abcdef", {2,4}]</pre>|<pre>"abcdef"[1:4]</pre>
uppercase|<pre>ToUpperCase["hello"]</pre>|<pre>"hello".upper()</pre>

