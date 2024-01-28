---
title: "Let's learn Python's re Module"
seoTitle: "Let's learn Python's re Module"
seoDescription: "Let's dive into Python's re module! Explore string manipulation, master regular expressions, and elevate our coding game. Let's learn together!"
datePublished: Sun Jan 28 2024 06:59:23 GMT+0000 (Coordinated Universal Time)
cuid: clrx5hem8000008l9669cfret
slug: lets-learn-pythons-re-module
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706424955858/619c3ad4-f30d-4bf7-aa81-3cea6ecbdccf.jpeg
tags: python, beginners, regex, string, regular-expressions, string-manipulation

---

Ever wished Python could effortlessly spot the details in a sea of text? Well, good news! Today, we're exploring the magic of `re` library. Ready to uncover the secrets? Let's dive in!

## re.match: Your Sidekick for Simple String Tricks

`re.match` is a versatile function in Python's `re` module that helps us determine if a string starts with a particular pattern. Think of it as a reliable guardian for your writing.

Let's dive into a simple example:

```python
import re

pattern = r'hello'
text = 'hello world'

result = re.match(pattern, text)

if result:
    print("Pattern found at the beginning of the text!")
else:
    print("Pattern not found at the beginning.")
```

In this case, the output would be "Pattern found at the beginning of the text!" since the string "hello world" starts with the pattern "hello."

### **Adding Flexibility with Anchors**

One of the strengths of `re.match` lies in its ability to work seamlessly with anchors. Anchors are special characters that denote the beginning **(**`^`**)** and end **(**`$`**)** of a line or string. For example:

```python
import re

pattern = r'^start'
text = 'start with re.match'

result = re.match(pattern, text)

if result:
    print("Pattern found at the beginning of the text!")
else:
    print("Pattern not found at the beginning.")
```

Here, the output would again be "Pattern found at the beginning of the text!" because the string starts with "start."

### **Wildcard and Quantifiers**

Sometimes, we might want to be more flexible in our matching. `re.match` allows us to use the wildcard `.` to represent any character and quantifiers like `*` or `+` to match multiple occurrences. For instance:

```python
import re

pattern = r'^\d+\s\w+'
text = '123 apples in the basket'

result = re.match(pattern, text)

if result:
    print("Pattern found at the beginning of the text!")
else:
    print("Pattern not found at the beginning.")
```

Here, the output would be `Pattern found at the beginning of the text!` as the string starts with one or more digits, followed by a space, and then a word.

## **Meet** `re.search`: Your New Best Friend

Up until now, we've been using `re.match` to find matches strictly at the beginning of a string. But now, let's introduce you to `re.search`, your new best friend. Imagine you're on a quest to find a specific word in a sentence – with `re.search`, it doesn't have to be at the beginning; it can be anywhere!

```python
import re

sentence = "I love coding in Python! It's such a fantastic language."

# Using re.search to find the word "Python"
search_result = re.search(r'Python', sentence)

if search_result:
    print("Found the word 'Python' in the sentence!")
else:
    print("Couldn't find the word 'Python'.")
```

Here, the output would be `Found the word 'Python in the sentence!`.

## **Finding All the Things with** `re.findall`

Now, suppose you want to find all the words ending in '**ing**,' not just the first one. Enter `re.findall`!

```python
import re

text = "Doing things, going home, staying awake, sleeping later"

# Using re.findall to find words ending with "ing"
ing_words = re.findall(r'\w+ing\b', text)

if ing_words:
    print("Found words ending with 'ing':", ing_words)
else:
    print("No words ending with 'ing' found.")
```

In this example, `re.findall` is employed with the pattern `\w+ing\b` to discover words ending with "ing" in the given text. If any such words are found, it prints "Found words ending with 'ing':", followed by the list of matching words. Otherwise, it prints "No words ending with 'ing' found."  
If we run this, we get this output:  
`Found words ending with 'ing': ['Doing', 'going', 'staying', 'sleeping']`

## **Decoding If/Then Sentences**

But what if you're dealing with sentences that have conditions, like "If this, then that"? We can still use `re.findall`, but let's be a bit clever:

```python
import re

sentence = ("If I'm not in a hurry, then I should stay. " +
            "On the other hand, if I leave, then I can sleep.")

# Using re.findall to extract conditions between 'If' and 'then'
conditions = re.findall(r'[Ii]f (.*?), then', sentence)

if conditions:
    print("Extracted conditions:", conditions)
else:
    print("No conditions found.")
```

Let's break the regular expression pattern :

```python
pattern = r'[Ii]f (.*?), then'
```

1. **\[Ii\]f:** Matches 'If' or 'if' at the beginning of the condition.
    
2. **(.\*?):** Captures anything between 'If' and 'then.'
    
3. **, then:** Matches the text ', then' following the captured condition.
    

We will get this output: `Extracted conditions: ["I'm not in a hurry", 'I leave']`

## **Your Toolbox: Essential**`re` Functions

Now, let's explore some more handy tools in the `re` toolbox:

* `re.match(pattern, str)`
    
* `re.search(pattern, str)`
    
* `re.findall(pattern, str)`
    
* `re.finditer(pattern, str)`
    
* `re.sub(pattern, replacement, str, count=0)`
    

Each one has its superpower, like finding, searching, and even replacing words in a sentence. For example:

```python
newstr = re.sub(r'\b[Ss]he\b', 'he', str)
print(newstr)
```

This simple code swaps every "**she**" with "**he**" in a sentence!

### **Miscellaneous Tips**

If you find yourself using the same pattern often, you can precompile it for efficiency using `re.compile(pattern, flags=0)`. This turns the pattern into a special object for faster matching.

Don't forget flags for special operations, like `re.IGNORECASE`, `re.MULTILINE`, and `re.DOTALL`. They can make your patterns more versatile.