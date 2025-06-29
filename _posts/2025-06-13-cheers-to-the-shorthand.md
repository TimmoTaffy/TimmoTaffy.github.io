---
layout: post
title:  "Cheers to the Shorthand!"
date:   2025-06-13 21:06:00 +0800
categories: computer-related
---

In *Data Structures & Algorithms in Python (Goodrich et al)*, there exists the following content:

> Section 1.9.2 introduces the topic of list comprehension, using an example such as 
> ```python
> squares = [ k k for k in range(1, n+1) ]
> ```
> as a shorthand for
> ```python
> squares = [ ]
> for k in range(1, n+1):
>   squares.append(k*k)
> ```
> Experiments should show that the list comprehension syntax is significantly faster than building the list by repeatedly appending (see Exercise C-5.23).

So what is a "shorthand"? Uh?

WHAT is a Shorthand?

Lemme tell you, a "shorthand" is supposed to be that chill friend who says "Yooo I'm here to make things easier", not the one who insists on a marathon while you're just trying to enjoy a casual 5k.

List comprehension *is* faster. But did it *really* need to make me feel that bad about my trusty for loop? I wasn't asking for a *race* - what I want is just cleaner syntax! Now I feel so bad like I'm being judged every time I write `for i in range`.

*Whew...*

Okay, fine, let's give credit where it's due. List comprehension *is* elegant, concise, faster, and will make you as smart as you actually are. So here's to list comprehension who I never asker for but perhaps unconsciously needed.

```python
print("Cheers")

>> Cheers
```  
  
  
By the way, below is another duel that worth noticing:
  
Instead of doing
```python
# WARNING: omega(n^2), do not do this
letters =
for c in document:
    if c.isalpha( ):
        letters += c    # creates a new instance if no other
                        # references to this string is detected 
```

we do
```python
# O(n)
temp = [ ]
for c in document:
    if c.isalpha( ):
        temp.append(c)
letters = .join(temp)
```