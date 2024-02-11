# Title (replace with your title)

We're going to walk through how to do regex.  Something I'm not very strong on, either.  Together we're going to understand many parts of regex.  This is a learnign experience for me as well as a gist for you!

## Summary

This tutorial highlights a nifty regex crafted specifically for sniffing out valid email addresses. It's like a Sherlock Holmes for emails, searching for the protagonist username, trailed by the trusty "@" symbol, and finally, the domain name. Oh, and it's not one to overlook those sneaky top-level domain extensions either!


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
Alright, let's talk about regex anchors. Think of them as the anchor points in your regex journey, helping you pinpoint exactly where to start or end your search.

The caret symbol ^ is like the starting line for a race – it tells your regex to start looking from the beginning of a line.

On the flip side, the dollar sign $ is like the finish line tape – it signals your regex to stop searching at the end of a line.

So, with these anchors, you can make sure your regex doesn't go wandering off where it shouldn't. They keep your search focused and efficient, like a pro with a laser pointer. Go ahead, anchor away!


### Quantifiers

Now, let's chat about regex quantifiers. Picture them as the magnifying glass in your regex toolkit, helping you zoom in on exactly what you're looking for.

The asterisk * is like the "anything goes" wildcard – it matches zero or more occurrences of the preceding character or group. It's the chill surfer dude of quantifiers, just riding the waves of text, dude!

Then there's the plus sign +, which is like the enthusiastic cheerleader – it matches one or more occurrences of the preceding character or group. It's all about that positive energy, you know?

And let's not forget the question mark ? – it's like the curious cat, matching zero or one occurrence of the preceding character or group. Sometimes it's there, sometimes it's not, but it's always ready for an adventure!

So, with these quantifiers, you can adjust the intensity of your regex search, whether you're looking for a little or a lot. Happy hunting!

Let's say we have a string that contains various numbers and we want to extract all sequences of digits from it. We can use quantifiers to match different patterns of digits:

\d?          # Matches zero or one digit
\d+          # Matches one or more digits
\d*          # Matches zero or more digits
\d{3}        # Matches exactly three digits
\d{2,4}      # Matches between two to four digits


### OR Operator

Let's dive into the world of regex OR operators! Think of them as the ultimate decision makers in your regex adventure, giving you the power to choose between different options.

The vertical bar | is like a magical fork in the road – it lets your regex take different paths, matching either one option or another. It's like having multiple doors to choose from, but you only need one key to unlock them all!

For example, if you're searching for words that can be spelled differently in American and British English, like "color" and "colour", you can use the OR operator like this: colou?r. This regex will match both "color" and "colour

P|p

P: Matches the uppercase letter "P".
p: Matches the lowercase letter "p".
Combined with the OR operator |, this regex will match either the uppercase or lowercase letter "P" in a string. So, it will match "P" or "p".

### Character Classes

Let us now move on to regex character classes – they're like the VIP sections in a regex club, reserved for special characters with specific roles.

Inside square brackets [], you can list characters or ranges of characters that you want your regex to match. It's like having a guest list for your regex party!

For example, if you're looking for vowels in a string, you can use the character class `[aeiou]`. This tells your regex to match any single character that is either 'a', 'e', 'i', 'o', or 'u'. It's like having a secret handshake for all the cool vowels out there!

And if you want to match any digit, you can use the shorthand \d, which is equivalent to [0-9]. It's like having a shortcut to the digits section of your character class VIP lounge!

So, with character classes, you can define custom groups of characters to match in your regex patterns, making your searches more precise and efficient. Party on, regex style!

### Flags

Regex flags are like the secret sauce that adds extra flavor to your regex recipes!

Regex flags are special modifiers that you can add at the end of your regex pattern to change how it behaves. They're like the volume knob on your stereo, giving you control over the intensity of your regex search.

For example, the `i` flag is like the chill vibe button – it makes your regex case-insensitive, so it doesn't care whether letters are uppercase or lowercase. It's like saying, 'Hey, regex, just go with the flow, man!'

Then there's the `g` flag, which is like the party mode switch – it makes your regex search globally throughout the entire string, instead of stopping at the first match. It's like telling your regex to keep on dancing until the music stops!

And let's not forget the `m` flag, which is like the multiline maestro – it changes how the `^` and `$` anchors work, allowing them to match the start and end of each line in a multiline string. It's like giving your regex a map to navigate through the text.

So, with regex flags, you can fine-tune your regex patterns to suit your specific needs, whether you're searching for a chill vibe, ready to party, or exploring new territories. Let the regex flags fly high!

Here's a Javascript example I found online using the `g` and `i` flags.
```
const str = "The quick brown fox jumps over the lazy dog. Foxes are cunning animals.";
const wordToFind = "fox";
const regex = new RegExp(wordToFind, "gi");

const matches = str.match(regex);

console.log(matches);
```


### Grouping and Capturing

Regex grouping and capturing – they're like the dynamic duos in your regex squad, working together to accomplish amazing feats!

Grouping in regex is like putting characters in parentheses `( )` to create a mini-team within your regex pattern. It's like forming a special club where certain characters stick together and follow the same rules.

For example, if you want to match different variations of a word, you can use grouping like this: `(cat|dog)`. This tells your regex to match either 'cat' or 'dog'. It's like saying, 'Hey, regex, these characters are besties – they come as a package deal!'

Capturing, on the other hand, is like giving your group a name and a mission. When you wrap a group in parentheses, your regex not only matches the characters inside the group but also remembers them for later. It's like taking a mental snapshot of your group's adventures along the way!

For example, if you want to extract specific parts of a string, you can use capturing groups like this: `(\d{3})-(\d{3})-(\d{4})`. This captures three groups of three digits each separated by hyphens, like in a phone number. It's like saying, 'Hey, regex, remember these digits – they're important for our next mission!'

So, with grouping and capturing, you can organize your regex patterns into powerful teams and extract valuable information from your strings. It's like having your own regex superheroes ready to save the day! Go, team regex!

If I wanted to use capture groups to get a date in several formats, we could do this using a match like this:

`Today is 10-02-2024, and yesterday was 2024/02/09.`

Our regex to find the dates would be below:
`/(\d{2})-(\d{2})-(\d{4})|(\d{4})\/(\d{2})\/(\d{2})/g`

That is a very complicated group, but once you know how it works it becomes easy.  Let's break it down.
We're looking for groups of 2, then 2, then 4 numbers OR 4, then 2, then 2.  The /g tells it to keep on going until the end, finding all occurences globally.

### Bracket Expressions

Bracket Expressions are like the custom playlists in your regex party, allowing you to group characters or ranges of characters together in a single expression.

Bracket expressions, denoted by square brackets `[ ]`, let you specify a set of characters you want your regex to match. It's like creating your own personal club of characters, where only the ones on the guest list get in!

For example, if you're looking for vowels in a string, you can use a bracket expression like `[aeiou]`. This tells your regex to match any single character that is either 'a', 'e', 'i', 'o', or 'u'. It's like having a VIP section reserved just for the coolest vowels in town!

And if you want to match any digit, you can use a shorthand like `[0-9]`, which matches any single digit from 0 to 9. It's like having a backstage pass to the digits party!

So, with bracket expressions, you can create custom groups of characters to match in your regex patterns, making your searches more tailored and efficient. It's like curating the perfect playlist for your regex dance floor!

Example:
"Hello, how are you?"

Let's apply the following regex expression:

`/[aeiou]/ig`

This tells the regex to match any single character that is either 'a', 'e', 'i', 'o', or 'u'.

The `i` flag makes the matching case-insensitive.
the `g` flag makes it global, and keeps on moving after a match is found

This would basically return `eooaeou`, as those are the vowels in our starting string.

### Greedy and Lazy Match

I hope the similes aren't getting to you.  Greedy vs. Lazy match; They're like the Goldilocks and the Three Bears of your regex world, each with its own preference for how much text to match.

Greedy matching is like Goldilocks going for the biggest bowl of porridge – it tries to match as much text as possible while still allowing the overall pattern to match. It's like saying, 'Give me all the text you can find, and then we'll see if it fits!'

On the other hand, lazy matching is like Goldilocks being more cautious, opting for the smallest bowl of porridge – it tries to match as little text as possible while still allowing the overall pattern to match. It's like saying, 'I'll take just enough text to satisfy the pattern, nothing more, nothing less!'

For example, let's say you have a string containing HTML tags like `<b>Hello</b> <i>world</i>`. If you use a greedy quantifier like `.*` to match the content between the `<b> and </b>` tags, it will greedily consume everything up to the last `</b>` tag, matching the entire string "Hello</b> <i>world". However, if you use a lazy quantifier like `.*?`, it will lazily match only the text "Hello" before the first `</b>` tag.

So, with greedy and lazy matching, you can control how much text your regex consumes, whether you're feeling adventurous like Goldilocks or more cautious. Just remember, there's no one-size-fits-all – sometimes you need to try a few bowls of porridge before you find the perfect match!

Here's a Javascript code example:
```
const htmlString = "<b>Hello</b> <i>world</i>";
const greedyRegex = /<b>(.*)<\/b>/; // Greedy quantifier .* matches as much as possible
const lazyRegex = /<b>(.*?)<\/b>/;  // Lazy quantifier .*? matches as little as possible

const greedyMatch = htmlString.match(greedyRegex);
const lazyMatch = htmlString.match(lazyRegex);

console.log("Greedy match:", greedyMatch[1]); // Prints "Hello</b> <i>world"
console.log("Lazy match:", lazyMatch[1]);     // Prints "Hello"
```


### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
