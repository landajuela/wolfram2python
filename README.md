# Wolfram ↔ Python

Welcome to **Wolfram ↔ Python**, a quick reference guide that mirrors common Wolfram Language constructs with their closest Python equivalents. Whether you’re coming from Mathematica and want to prototype logic in Python, or you’re a Pythonista looking to explore Wolfram’s powerful symbolic and functional paradigms, this cheat-sheet will help you translate ideas between the two ecosystems at a glance. Each section groups related operations—everything from basic functions and data structures to functional and procedural programming patterns—so you can jump straight to what you need. Enjoy seamless code translation and unleash the strengths of both languages!

## General

 Name | Wolfram | Python
:---:|:---|:---
range|<pre>{Range[0,7],Range[0,7,2]}</pre>|<pre>[range(0,7+1),range(0,7+1,2)]</pre>
func|<pre>f[x_]:=x+2;f[2]</pre>|<pre>def f(x):<br/>	return 2 + x<br/>f(2)<br/></pre>
global|<pre>Names["Global`*"]</pre>|<pre>globals()</pre>
print|<pre>Print["Hello world"]</pre>|<pre>print("Hello world")</pre>
print val|<pre>Print["val="<>ToString[5]]</pre>|<pre>print(f"val={str(5)}")</pre>
counter|<pre>Counts[{1,1,2,2,2,4}]</pre>|<pre>from collections import Counter<br/>dict(Counter([1,1,2,2,2,4]))<br/></pre>
add to|<pre>i=2;i+=1;i</pre>|<pre>i=2;i+=1;i</pre>
help|<pre>?Sort</pre>|<pre>help(sorted)</pre>
null|<pre>None</pre>|<pre>None</pre>

## List

 Name | Wolfram | Python
:---:|:---|:---
list|<pre>{2,2,9,6,7}</pre>|<pre>[2,2,9,6,7]</pre>
append to list|<pre>l={2, 2, 9, 6, 7}; AppendTo[l,2];l</pre>|<pre>l=[2, 2, 9, 6, 7]; l.append(2); l</pre>
insert to list|<pre>l={2,2,9,6,7};l=Insert[l,3,1+1];l</pre>|<pre>l=[2, 2, 9, 6, 7]; l.insert(1,3);l</pre>
pop from list|<pre>l={2,2,9,6,7};l=Drop[l,-1];l</pre>|<pre>l=[2,2,9,6,7];l.pop();l</pre>
extend list|<pre>l={2,2,9,6,7};l=Join[l,{5,6}];l</pre>|<pre>l=[2, 2, 9, 6, 7];l.extend([5, 6]);l</pre>
slice list|<pre>l={2,2,9,6,7};{l[[;;]],l[[1+1;;]],l[[0+1;;-1-1;;2]],l[[1;;-1;;2]]}</pre>|<pre>l=[2, 2, 9, 6, 7];[l[:],l[1::],l[0:-1:2],l[::2]]</pre>
length of list|<pre>Length[{2, 2, 9, 6, 7}]</pre>|<pre>len([2, 2, 9, 6, 7])</pre>
join lists|<pre>{1,2}~Join~{3,4}</pre>|<pre>[1,2]+[3,4]</pre>
zip 2 lists|<pre>Transpose[{{"a", "b", "c", "d", "e"},{2, 2, 9, 6, 7}}]</pre>|<pre>zip(["a", "b", "c", "d", "e"],[2, 2, 9, 6, 7])</pre>
get element position|<pre>Position[{a,b,a,a,b,c,b},b]</pre>|<pre>[[i + 1] for i,v in enumerate(['a','b','a','a','b','c','b']) if v == 'b']</pre>
random sample|<pre>RandomSample[{1,2,3,4}, 2]</pre>|<pre>import random;random.sample([1,2,3,4], 2)</pre>
reverse list (out-of-place)|<pre>Reverse[{1,2,3}]</pre>|<pre>list(reversed([1,2,3]))</pre>
reverse list (slicing, out-of-place)|<pre>{1,2,3}[[-1;;1;;-1]]</pre>|<pre>[1,2,3][::-1]</pre>
reverse list (in-place)|<pre>Reverse[{1,2,3}]</pre>|<pre>l=[1,2,3];l.reverse();l</pre>
unique in list (non-stable)|<pre>DeleteDuplicates[{9, 2, 2, 9, 6}]</pre>|<pre>list(set([9, 2, 2, 9, 6]))</pre>
unique in list (stable)|<pre>DeleteDuplicates[{2, 2, 9, 6}]</pre>|<pre>seen = set(); [x for x in [2,2,9,6] if not (x in seen or seen.add(x))]</pre>
sort list (stable, out-of-place)|<pre>words = {"apple", "bat", "banana", "car"};<br/>ReverseSortBy[words,{StringLength,(-Position[words,#][[1]]&)}]<br/></pre>|<pre>words = ["apple", "bat", "banana", "car"]<br/>sorted(words, key=len, reverse=True)<br/></pre>
sort list (stable,in-place)|<pre>words = {"apple", "bat", "banana", "car"};<br/>ReverseSortBy[words,{StringLength,(-Position[words,#][[1]]&)}]<br/></pre>|<pre>words = ["apple", "bat", "banana", "car"]<br/>words.sort(key=len, reverse=True);words<br/></pre>

## List of lists

 Name | Wolfram | Python
:---:|:---|:---
list of lists|<pre>{{1,2},{3,4}}</pre>|<pre>[[1,2],[3,4]]</pre>
extract column (ll)|<pre>l={{1,2},{3,4,5}};l[[All,2]]</pre>|<pre>l=[[1,2],[3,4,5]]; [row[1] for row in l]</pre>
sorted (ll)|<pre>l = {{"b", 3},{"a", 5},{"a", 4},{"b", 2}};SortBy[l, {First, Last}]</pre>|<pre>l=[["b",3],["a",5],["a",4],["b",2]];sorted(l,key=lambda item : [item[0],item[1]])</pre>
flatten nested|<pre>Flatten[{{1,2},{3,4}}]</pre>|<pre>l=[[1, 2], [3, 4]]; [x for sub in l for x in sub]</pre>
partition/chunk|<pre>Partition[{1,2,3,4,5,6,7}, UpTo[2]]</pre>|<pre>l = [1,2,3,4,5,6,7]; [l[i:i+2] for i in range(0, len(l), 2)]</pre>

## Dict

 Name | Wolfram | Python
:---:|:---|:---
dict|<pre><\|"a" -> 2, "b" -> 2, "c" -> 9, "d" -> 6, "e" -> 7\|></pre>|<pre>{"a": 2, "b": 2, "c": 9, "d": 6, "e": 7}</pre>
access element in dict|<pre><\|"a" -> 2, "b" -> 2, "c" -> 9, "d" -> 6, "e" -> 7\|>["a"]</pre>|<pre>{"a": 2, "b": 2, "c": 9, "d": 6, "e": 7}["a"]</pre>
add or update key|<pre>d = <\|"a" -> 1\|>; d["b"] = 2; d</pre>|<pre>d = {"a": 1}; d["b"] = 2; d</pre>
remove key|<pre>KeyDrop[<\|"a" -> 1, "b" -> 2\|>, "a"]</pre>|<pre>d = {"a": 1, "b": 2};d.pop("a"); d</pre>
get keys|<pre>Keys[<\|"a"->1, "b"->2\|>]</pre>|<pre>d = {"a": 1, "b": 2}; d.keys()</pre>
get values|<pre>Values[<\|"a"->1, "b"->2\|>]</pre>|<pre>d = {"a": 1, "b": 2}; d.values()</pre>
get key-values|<pre>d=<\|"a"->1, "b"->2\|>;MapApply[{#1,#2}&,Normal[d]]</pre>|<pre>d = {"a": 1, "b": 2}; d.items()</pre>
sort by key|<pre>d=<\|"b"->2,"a"->1,"c"->3\|>; KeySort[d]</pre>|<pre>d = {'b': 2, 'a': 1, 'c': 3}; dict(sorted(d.items()))</pre>
sort by value|<pre>d=<\|"b"->2,"a"->1,"c"->3\|>; Association@SortBy[Normal[d],#[[-1]]&]</pre>|<pre>d = {'b': 2, 'a': 1, 'c': 3}; dict(sorted(d.items(), key=lambda kv: kv[1]))</pre>
merge dict out-of-place|<pre>a=<\|"b"->2,"a"->1,"c"->3\|>;b=<\|"d"->2,"e"->1,"c"->4\|>;Join[a,b]</pre>|<pre>a={"b":2,"a":1,"c":3};b={"d":2,"e":1,"c": 4};a \| b</pre>
merge dict in-place|<pre>a=<\|"b"->2,"a"->1,"c"->3\|>;b=<\|"d"->2,"e"->1,"c"->4\|>;AssociateTo[a,b];a</pre>|<pre>a={"b":2,"a":1,"c":3};b={"d":2,"e":1,"c": 4};a.update(b);a</pre>
unpack a dictionary|<pre>Association["A"->1,Table[ToString[i]->i,{i,2,3}],"J"->4]</pre>|<pre>{"A": 1, **{str(i): i for i in range(2, 3+1)}, "J": 4}</pre>

## List of dicts

 Name | Wolfram | Python
:---:|:---|:---
list of dicts|<pre>{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}</pre>|<pre>[{"a": 1, "b": 2},{"a": 3, "b": 4}]</pre>
extract column from ld|<pre>d={<\|"a"->1,"b"->2,"c"->5\|>,<\|"a"->3,"b"->4\|>};d[[All,"b"]]</pre>|<pre>d = [{"a": 1, "b": 2, "c": 5},{"a": 3, "b": 4}]; [elem["b"] for elem in d]</pre>
select entry in ld|<pre>people={<\|"name"->"John","age"->25\|>,<\|"name"->"Jane","age"->30\|>};Select[people,(#["name"]=="John")&]</pre>|<pre>people=[{'name': 'John', 'age': 25},{'name': 'Jane', 'age': 30}]<br/>[elem for elem in people if elem['name'] == 'John']<br/></pre>
sort ld by entry|<pre>people={<\|"name"->"John","age"->45\|>,<\|"name"->"Jane","age"->30\|>};SortBy[people,#"age"&]</pre>|<pre>people=[{'name': 'John', 'age': 45},{'name': 'Jane', 'age': 30}]<br/>sorted(people,key=lambda item : item['age'])<br/></pre>

## Set

 Name | Wolfram | Python
:---:|:---|:---
initialization empty|<pre>(* Mathematica doesn’t have a built-in hash-set; use a list { } and Unique[*] if you must *)</pre>|<pre>s = set()</pre>
initialization from iterable|<pre>s={1,2,2,2,3,3};s=DeleteDuplicates[s];s</pre>|<pre>s=set([1,2,2,2,3,3]);s</pre>
add element|<pre>s={1,2,2,2,3,3};s=DeleteDuplicates[s];AppendTo[s,5]</pre>|<pre>s=set([1,2,2,2,3,3]);s.add(5);s</pre>
add multiple elements|<pre>s={1,2,2,2,3,3};s=DeleteDuplicates[s];Union[s,{5,6}]</pre>|<pre>s=set([1,2,2,2,3,3]);s.update([5,6]);s</pre>
remove element (error if absent)|<pre>s={1,2,2,2,3,3};s=DeleteDuplicates[s];DeleteElements[s,{2}]</pre>|<pre>s=set([1,2,2,2,3,3]);s.remove(2);s</pre>
remove element safely|<pre>s={1,2,2,2,3,3};s=DeleteDuplicates[s];DeleteElements[s,{4}]</pre>|<pre>s=set([1,2,2,2,3,3]);s.discard(4);s</pre>
union|<pre>Union[{1,2,3},{3,4,5}]</pre>|<pre>{1,2,3} \| {3,4,5}</pre>
intersection|<pre>Intersection[{1,2,3},{3,4,5}]</pre>|<pre>{1,2,3} & {3,4,5}</pre>
difference|<pre>Complement[{1,2,3},{3,4,5}]</pre>|<pre>{1,2,3} - {3,4,5}</pre>
symmetric difference|<pre>SymmetricDifference[{1,2,3},{3,4,5}]</pre>|<pre>{1,2,3} ^ {3,4,5}</pre>
membership test|<pre>MemberQ[{1,2,3}, 3]</pre>|<pre>3 in {1,2,3}</pre>

## Deque

 Name | Wolfram | Python
:---:|:---|:---
initialize empty|<pre>q = CreateDataStructure["Deque"]</pre>|<pre>from collections import deque;q=deque()</pre>
peek front|<pre>q=CreateDataStructure["Deque",{3,2}];q["PeekFront"]</pre>|<pre>from collections import deque;q=deque([3,2]);q[0]</pre>
enqueue (push to right)|<pre>q=CreateDataStructure["Deque"];q["PushBack",2];<br/>q["PushBack",3];q["PushBack",4];q["PeekFront"]<br/></pre>|<pre>from collections import deque;q=deque();q.append(2);<br/>q.append(3);q.append(4);q[0]<br/></pre>
dequeue (pop from front)|<pre>q=CreateDataStructure["Deque",{2,3,4}];q["PopFront"]</pre>|<pre>from collections import deque;q=deque([2,3,4]);q.popleft()</pre>
get length|<pre>q=CreateDataStructure["Deque",{2,3,4}];q["Length"]</pre>|<pre>from collections import deque;q=deque([2,3,4]);len(q)</pre>
clear queue|<pre>ds["DropAll"]</pre>|<pre>q.clear()</pre>

## Equivalence

 Name | Wolfram | Python
:---:|:---|:---
map & comprehension|<pre>Map[#^2&,{1,2,3,4}]==Table[x^2,{x,{1,2,3,4}}]</pre>|<pre>list(map(lambda x: x**2, [1,2,3,4])) == [x**2 for x in [1,2,3,4]]</pre>
filter & comprehension|<pre>Select[{1, 2, 3, 4}, (Mod[#,2]==0)&]==Table[If[Mod[x,2]==0,x,Nothing],{x,{1,2,3,4}}]</pre>|<pre>list(filter(lambda x: x % 2 == 0, [1,2,3,4])) == [x for x in [1,2,3,4] if x % 2 == 0]</pre>

## Functional programming

 Name | Wolfram | Python
:---:|:---|:---
func nest|<pre>NestList[#^2&,2,4]</pre>|<pre>from functools import reduce<br/>def nest_list(f, x, n):<br/>    return [reduce(lambda acc, _: f(acc), range(i), x) for i in range(n+1)]<br/>nest_list(lambda v: v**2, 2, 4)<br/></pre>
map|<pre>Map[2+#&,{2,2,9,6,7}]</pre>|<pre>map(lambda x : 2 + x, [2, 2, 9, 6, 7])</pre>
map comprehension|<pre>Table[2 + x, {x, {2, 2, 9, 6, 7}}]</pre>|<pre>[2 + x for x in [2, 2, 9, 6, 7]]</pre>
select/filter|<pre>Select[{1, 2, 3, 4}, (Mod[#,2]==0)&]</pre>|<pre>filter(lambda x: x % 2 == 0, [1,2,3,4])</pre>
select/filter
comprehension|<pre>Table[If[Mod[x,2]==0,x,Nothing],{x,{1,2,3,4}}]</pre>|<pre>[x for x in [1,2,3,4] if x % 2 == 0]</pre>
fold (reduce)|<pre>Fold[Plus, 0, {1,2,3,4}]</pre>|<pre>from functools import reduce<br/>reduce(lambda a,b: a+b, [1,2,3,4], 0)<br/></pre>
nest (reduce)|<pre>Nest[#/2&, 16., Log[2,16]]</pre>|<pre>from functools import reduce; import math<br/>reduce(lambda acc, _: acc / 2, range(int(math.log(16, 2))), 16)<br/></pre>
anonymous function|<pre>#^2&[2]</pre>|<pre>(lambda x: x**2)(2)</pre>
anonymous function (2D)|<pre>(#1 + #2)&[1,2]</pre>|<pre>(lambda x, y: x + y)(1, 2)</pre>

## Procedural programming

 Name | Wolfram | Python
:---:|:---|:---
if|<pre>If[3>2,Print["true"]]</pre>|<pre>if 3 > 2:<br/>    print("true")<br/></pre>
if assign|<pre>If[3 < 2, 3, 2]</pre>|<pre>3 if 3 < 2 else 2</pre>
for loop|<pre>Do[Print[i], {i, 1, 5}]</pre>|<pre>for i in range(1,6):<br/>    print(i)<br/></pre>
while loop|<pre>i = 0; While[i < 5, i++; Print[i]]</pre>|<pre>i = 0<br/>while i < 5:<br/>    i += 1<br/>    print(i)<br/></pre>
break/exit loop|<pre>For[i = 1, i < 10, i++, If[i > 5, Break[]]]</pre>|<pre>for i in range(1,10):<br/>    if i > 5: break<br/></pre>

## Dataframe

 Name | Wolfram | Python
:---:|:---|:---
dataset/dataframe|<pre>Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}]</pre>|<pre>import pandas as pd<br/>pd.DataFrame([{"a": 1, "b": 2}, {"a": 3, "b": 4}])<br/></pre>
extract value from df|<pre>df = Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}];<br/>{df[[1,"b"]],df[[1,"b"]],df[[1]]["b"],df[[All,"b"]][1],df[[All,"b"]][[1]]}<br/></pre>|<pre>import pandas as pd<br/>df = pd.DataFrame([{"a": 1, "b": 2}, {"a": 3, "b": 4}])<br/>[df.loc[0, "b"], df.at[0, "b"], df.iloc[0]["b"], df["b"].iloc[0], df["b"].iat[0]]<br/></pre>
extract column from df|<pre>df = Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}];<br/>df[All, "a"]<br/></pre>|<pre>import pandas as pd<br/>df = pd.DataFrame([{"a": 1, "b": 2}, {"a": 3, "b": 4}])<br/>list(df["a"].values)<br/></pre>
extract multiple columns|<pre>df = Dataset[{<\|"a"->1,"b"->2,"c"->4\|>,<\|"a"->3,"b"->4,"c"->5\|>}];<br/>df[All, {"a", "b"}]<br/></pre>|<pre>import pandas as pd<br/>df = pd.DataFrame([{"a": 1, "b": 2, "c": 3}, {"a": 3, "b": 4, "c": 5}])<br/>df[["a", "b"]]<br/></pre>
extract row|<pre>df = Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}];<br/>df[1]<br/></pre>|<pre>import pandas as pd<br/>df = pd.DataFrame([{"a": 1, "b": 2}, {"a": 3, "b": 4}])<br/>df.iloc[0]<br/></pre>
remove/drop columns|<pre>df = Dataset[{<\|"a"->1,"b"->2,"c"->4\|>,<\|"a"->3,"b"->4,"c"->5\|>}];<br/>df[All, KeyDrop["c"]]<br/></pre>|<pre>import pandas as pd<br/>df=pd.DataFrame([{"a": 1, "b": 2, "c": 4}, {"a": 3, "b": 4, "c": 5}])<br/>df.drop(columns=["c"])<br/></pre>
select/filter rows|<pre>df = Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}];<br/>df[Select[#["a"]>1&&#["b"]>1&]]<br/></pre>|<pre>import pandas as pd<br/>df=pd.DataFrame([{"a": 1, "b": 2},{"a": 3, "b": 4},{"a": 2, "b": -1}])<br/>df[(df["a"] > 1) & (df["b"] > 1)]<br/></pre>
transform column|<pre>df = Dataset[{<\|"a"->1,"b"->2,"c"->4\|>,<\|"a"->3,"b"->4,"c"->5\|>}];<br/>df[All,Association[#,"b"->(#["b"]^2)]&]<br/></pre>|<pre>import pandas as pd<br/>df=pd.DataFrame([{"a": 1, "b": 2, "c": 4}, {"a": 3, "b": 4, "c": 5}])<br/>df["b"] = df["b"].apply(lambda x:x**2); df<br/></pre>
append vectorized column|<pre>df = Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}];<br/>df[All, Append[#, "c" -> #a + #b] &]<br/></pre>|<pre>import pandas as pd<br/>df = pd.DataFrame([{"a": 1, "b": 2}, {"a": 3, "b": 4}])<br/>df["c"] = df["a"] + df["b"];df<br/></pre>
append new column|<pre>df = Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}];<br/>df[All, Append[#, "a_sq" -> (#a)^2] &]<br/></pre>|<pre>import pandas as pd<br/>df = pd.DataFrame([{"a": 1, "b": 2}, {"a": 3, "b": 4}])<br/>df["a_sq"] = df["a"].apply(lambda x: x**2);df<br/></pre>
method chaining|<pre>df = Dataset[{<\|"a"->1,"b"->2\|>,<\|"a"->3,"b"->4\|>}];<br/>ds2 = Select[df, #a > 1 &];<br/>ds3 = ds2[All, Append[#, "d" -> #a * #b] &];<br/>ds3[All, {"a", "b", "d"}]<br/></pre>|<pre>import pandas as pd<br/>df = pd.DataFrame([{"a": 1, "b": 2}, {"a": 3, "b": 4}])<br/>(df[df["a"] > 1]<br/>   .assign(d=lambda x: x["a"] * x["b"])<br/>   .loc[:, ["a", "b", "d"]])<br/></pre>

## String

 Name | Wolfram | Python
:---:|:---|:---
string format|<pre>ToString[StringForm["The values are x=`` and y=``.", 5, 10]]</pre>|<pre>"The values are x={} and y={}.".format(5, 10)</pre>
string join|<pre>StringRiffle[{2, 2, 9, 6, 7}, " "]</pre>|<pre>' '.join(["2", "2", "9", "6", "7"])</pre>
substring|<pre>StringTake["abcdef", {2,4}]</pre>|<pre>"abcdef"[1:4]</pre>
string length|<pre>StringLength["hello"]</pre>|<pre>len("hello")</pre>
uppercase|<pre>ToUpperCase["hello"]</pre>|<pre>"hello".upper()</pre>
replace substring|<pre>StringReplace["a_b_c", "_"->"-"]</pre>|<pre>"a_b_c".replace("_","-")</pre>
string starts|<pre>{StringStartsQ["beach", "_"],StringStartsQ["beach", "b"]}</pre>|<pre>["beach".startswith('_'),"beach".startswith('b')]</pre>
sort|<pre>sl={"s2","s10","s50","a"};<br/>SortBy[sl,StringCases[#,x:(DigitCharacter..\|LetterCharacter..):>If[<br/>StringMatchQ[x,DigitCharacter..],ToExpression[x],ToLowerCase[x]]]&]<br/></pre>|<pre>import re;sl=["s2","s10","s50","a"];<br/>sorted(sl, key=lambda s : [int(t) if t.isdigit() else t.lower() for t in re.split(r'(\d+)', s)])<br/></pre>

## Math

 Name | Wolfram | Python
:---:|:---|:---
factorial|<pre>Factorial[7]</pre>|<pre>import math; math.factorial(7)</pre>
square root|<pre>Sqrt[9]</pre>|<pre>import math; math.sqrt(9)</pre>
total|<pre>Total[{2, 2, 9, 6, 7}]</pre>|<pre>sum([2, 2, 9, 6, 7])</pre>
mod|<pre>Mod[30,12]</pre>|<pre>30 % 12</pre>
floor division|<pre>{Floor[(3 + 4) / 2], Floor[(-3 - 4) / 2]}</pre>|<pre>[(3 + 4) // 2, (-3 - 4) // 2]</pre>
max|<pre>{Max[2,3], Max[{2,7,3}]}</pre>|<pre>[max(2,3), max([2,7,3])]</pre>
accumulate|<pre>Accumulate[{1,2,3,4,5}]</pre>|<pre>from itertools import accumulate<br/>list(accumulate([1, 2, 3, 4, 5]))<br/></pre>

## Logic

 Name | Wolfram | Python
:---:|:---|:---
logical AND / OR / NOT|<pre>a=3; b=5; {a < b && b > 4, a > b \|\| b == 5, ! (a == b)}</pre>|<pre>a = 3; b = 5; [a < b and b > 4, a > b or b == 5, not (a == b)]</pre>
short-circuit behaviour|<pre>a = False; b = Print["hi"]; a && b</pre>|<pre>a = False<br/> def f():<br/>     print("hi"); return True<br/>print(a and f())<br/></pre>
chaining comparisons & logic|<pre>x = 10; {0 < x < 15 && ! (x < 5 \|\| x > 20)}</pre>|<pre>x = 10; [0 < x < 15 and (not (x < 5 or x > 20))]</pre>

## Regex

 Name | Wolfram | Python
:---:|:---|:---
basic match|<pre>StringMatchQ["hello123", RegularExpression["^[a-z]+\d+"]]</pre>|<pre>import re<br/>bool(re.match(r"^[a-z]+\d+", "hello123"))<br/></pre>
findall digits|<pre>StringCases["ID: 4567 & Code: 890", RegularExpression["\d+"]]</pre>|<pre>import re<br/>re.findall(r"\d+", "ID: 4567 & Code: 890")<br/></pre>
replace whitespace|<pre>StringReplace["The rain in Spain", RegularExpression["\s+"] -> "_"]</pre>|<pre>import re<br/>re.sub(r"\s+", "_", "The rain in Spain")<br/></pre>
email validation|<pre>StringMatchQ["alice-b@google.com", RegularExpression["^[\w\.\-]+@[\w\.\-]+\.[a-zA-Z]{2,4}$"]]</pre>|<pre>import re<br/>bool(re.match(r"^[\w\.\-]+@[\w\.\-]+\.[a-zA-Z]{2,4}$", "alice-b@google.com"))<br/></pre>

## Parity Test

![Parity Test](images/parity_test.png)