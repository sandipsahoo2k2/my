# Java vs Python — Interview Cheat Sheet

This is the quick list of key difference or reference of methods key words that you need to know if you are coiming from java. 
If you have good hold of a language and Transitioning to AI you must master Python for your interview. This [link here](java_to_python.md) might be a extensive reference for your next interview.

## Key Language Constructs

| Concept | Java | Python |
|---------|------|--------|
| List comprehension | *(use streams or loop)* | `[x*2 for x in lst]` | Will create a new list with squared values
| Sort with key | `list.sort(Comparator.comparing(...))` | `list.sort(key=lambda x: x[1])` |
| 2D array init | `int[][] dp = new int[m][n];` | `dp = [[0]*n for _ in range(m)]` |
| Char to int | `(int) ch - 'a'` | `ord(ch) - ord('a')` |
| Int to char | `(char)('a' + i)` | `chr(ord('a') + i)` |
| Count freq (map) | `map.getOrDefault(k,0)+1` | `Counter(list)` from `collections` |

---

## Strings

| Java | Python |
|------|--------|
| `s.substring(a, b)` | `s[a:b]` |
| `s.trim()` | `s.strip()` |

---

## For Loops

| Concept | Java | Python |
|---------|------|--------|
| Step/increment | `for (int i = 0; i < n; i += 2)` | `for i in range(0, n, 2):` |
| Reverse | `for (int i = n-1; i >= 0; i--)` | `for i in range(n-1, -1, -1):` |
| For-each (array) | `for (int x : arr)` | `for x in arr:` |
| With index | `for (int i = 0; i < list.size(); i++)` | `for i, x in enumerate(list):` |
| Map entries | `for (Map.Entry<K,V> e : map.entrySet())` | `for k, v in d.items():` |

---

## ArrayList / List

| Java (ArrayList) | Python (list) |
|------------------|---------------|
| `list.add(x)` | `list.append(x)` |
| `list.set(i, x)` | `list[i] = x` |
| `list.remove(i)` | `list.pop(i)` |
| `Collections.reverse(list)` | `list.reverse()` |

---

## HashMap / dict

| Java (HashMap) | Python (dict) |
|----------------|---------------|
| `new HashMap<>()` | `{}` |
| `map.put(k, v)` | `d[k] = v` |
| `map.get(k)` | `d[k]` |
| `map.getOrDefault(k, def)` | `d.get(k, def)` |
| `map.containsKey(k)` | `k in d` |
| `map.remove(k)` | `del d[k]` / `d.pop(k)` |
| `map.keySet()` | `d.keys()` |
| `map.values()` | `d.values()` |
| `map.entrySet()` | `d.items()` |
---

## HashSet / set

| Java (HashSet) | Python (set) |
|----------------|--------------|
| `new HashSet<>()` | `set()` |
| `set.add(x)` | `s.add(x)` |
| `set.remove(x)` | `s.remove(x)` |
| `set.contains(x)` | `x in s` |

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

> Python: `from collections import deque` — use `deque` for O(1) popleft.

---

## Math

| Java | Python |
|------|--------|
| `Math.pow(x, n)` | `x ** n` |
| `Math.sqrt(x)` | `x ** 0.5` |
| `Math.floor(x)` | `math.floor(x)` |
| `Math.ceil(x)` | `math.ceil(x)` |

---

## Arrays

| Java | Python |
|------|--------|
| `Arrays.sort(arr)` | `arr.sort()` / `sorted(arr)` |
| `Arrays.fill(arr, x)` | `[x] * n` |
| `Arrays.copyOf(arr, n)` | `arr[:n]` |
| `Arrays.asList(arr)` | `list(arr)` |

---
