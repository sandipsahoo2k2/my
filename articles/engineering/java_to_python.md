# Java vs Python — Interview Cheat Sheet

## Key Language Constructs

| Concept | Java | Python |
|---------|------|--------|
| Null check | `x == null` | `x is None` |
| Ternary | `cond ? a : b` | `a if cond else b` |
| Print | `System.out.println(x)` | `print(x)` |
| Cast int | `(int) x` | `int(x)` |
| Integer division | `a / b` (int/int) | `a // b` |
| Modulo | `a % b` | `a % b` |
| Logical AND | `&&` | `and` |
| Logical OR | `\|\|` | `or` |
| Logical NOT | `!` | `not` |
| String format | `String.format("%d", n)` | `f"{n}"` |
| Swap | `int tmp=a; a=b; b=tmp;` | `a, b = b, a` |
| Multi-assign | `int a=0, b=0;` | `a = b = 0` |
| Infinity | `Integer.MAX_VALUE` | `float('inf')` |
| Type check | `x instanceof String` | `isinstance(x, str)` |
| List comprehension | *(use streams or loop)* | `[x*2 for x in lst]` |
| Sort with key | `list.sort(Comparator.comparing(...))` | `list.sort(key=lambda x: x[1])` |
| 2D array init | `int[][] dp = new int[m][n];` | `dp = [[0]*n for _ in range(m)]` |
| Char to int | `(int) ch - 'a'` | `ord(ch) - ord('a')` |
| Int to char | `(char)('a' + i)` | `chr(ord('a') + i)` |
| Count freq (map) | `map.getOrDefault(k,0)+1` | `Counter(list)` from `collections` |

---

## Strings

| Java | Python |
|------|--------|
| `s.length()` | `len(s)` |
| `s.charAt(i)` | `s[i]` |
| `s.substring(a, b)` | `s[a:b]` |
| `s.indexOf("x")` | `s.index("x")` / `s.find("x")` |
| `s.contains("x")` | `"x" in s` |
| `s.replace("a","b")` | `s.replace("a","b")` |
| `s.toUpperCase()` | `s.upper()` |
| `s.toLowerCase()` | `s.lower()` |
| `s.trim()` | `s.strip()` |
| `s.split(",")` | `s.split(",")` |
| `String.join(",", list)` | `",".join(list)` |
| `s.startsWith("x")` | `s.startswith("x")` |
| `s.endsWith("x")` | `s.endswith("x")` |
| `String.valueOf(n)` | `str(n)` |
| `Integer.parseInt(s)` | `int(s)` |

---

## For Loops

| Concept | Java | Python |
|---------|------|--------|
| Basic range | `for (int i = 0; i < n; i++)` | `for i in range(n):` |
| Range with start | `for (int i = a; i < b; i++)` | `for i in range(a, b):` |
| Step/increment | `for (int i = 0; i < n; i += 2)` | `for i in range(0, n, 2):` |
| Reverse | `for (int i = n-1; i >= 0; i--)` | `for i in range(n-1, -1, -1):` |
| For-each (array) | `for (int x : arr)` | `for x in arr:` |
| For-each (list) | `for (String s : list)` | `for s in list:` |
| With index | `for (int i = 0; i < list.size(); i++)` | `for i, x in enumerate(list):` |
| Map entries | `for (Map.Entry<K,V> e : map.entrySet())` | `for k, v in d.items():` |
| While loop | `while (condition) { }` | `while condition:` |
| Break | `break;` | `break` |
| Continue | `continue;` | `continue` |

---

## ArrayList / List

| Java (ArrayList) | Python (list) |
|------------------|---------------|
| `new ArrayList<>()` | `[]` |
| `list.add(x)` | `list.append(x)` |
| `list.add(i, x)` | `list.insert(i, x)` |
| `list.get(i)` | `list[i]` |
| `list.set(i, x)` | `list[i] = x` |
| `list.remove(i)` | `list.pop(i)` |
| `list.size()` | `len(list)` |
| `list.contains(x)` | `x in list` |
| `list.indexOf(x)` | `list.index(x)` |
| `Collections.sort(list)` | `list.sort()` |
| `Collections.reverse(list)` | `list.reverse()` |
| `list.clear()` | `list.clear()` |
| `list.isEmpty()` | `not list` |

---

## HashMap / dict

| Java (HashMap) | Python (dict) |
|----------------|---------------|
| `new HashMap<>()` | `{}` |
| `map.put(k, v)` | `d[k] = v` |
| `map.get(k)` | `d[k]` / `d.get(k)` |
| `map.getOrDefault(k, def)` | `d.get(k, def)` |
| `map.containsKey(k)` | `k in d` |
| `map.remove(k)` | `del d[k]` / `d.pop(k)` |
| `map.keySet()` | `d.keys()` |
| `map.values()` | `d.values()` |
| `map.entrySet()` | `d.items()` |
| `map.size()` | `len(d)` |

---

## HashSet / set

| Java (HashSet) | Python (set) |
|----------------|--------------|
| `new HashSet<>()` | `set()` |
| `set.add(x)` | `s.add(x)` |
| `set.remove(x)` | `s.remove(x)` / `s.discard(x)` |
| `set.contains(x)` | `x in s` |
| `set.size()` | `len(s)` |

---

## Stack / Queue / Deque

| Java | Python |
|------|--------|
| `stack.push(x)` | `stack.append(x)` |
| `stack.pop()` | `stack.pop()` |
| `stack.peek()` | `stack[-1]` |
| `queue.offer(x)` | `dq.append(x)` |
| `queue.poll()` | `dq.popleft()` |
| `queue.peek()` | `dq[0]` |
| `deque.addFirst(x)` | `dq.appendleft(x)` |
| `deque.addLast(x)` | `dq.append(x)` |

> Python: `from collections import deque` — use `deque` for O(1) popleft.

---

## Math

| Java | Python |
|------|--------|
| `Math.max(a, b)` | `max(a, b)` |
| `Math.min(a, b)` | `min(a, b)` |
| `Math.abs(x)` | `abs(x)` |
| `Math.pow(x, n)` | `x ** n` |
| `Math.sqrt(x)` | `x ** 0.5` |
| `Math.floor(x)` | `math.floor(x)` |
| `Math.ceil(x)` | `math.ceil(x)` |
| `Integer.MAX_VALUE` | `float('inf')` |
| `Integer.MIN_VALUE` | `float('-inf')` |

---

## Arrays

| Java | Python |
|------|--------|
| `Arrays.sort(arr)` | `arr.sort()` / `sorted(arr)` |
| `Arrays.fill(arr, x)` | `[x] * n` |
| `arr.length` | `len(arr)` |
| `Arrays.copyOf(arr, n)` | `arr[:n]` |
| `Arrays.asList(arr)` | `list(arr)` |

---
