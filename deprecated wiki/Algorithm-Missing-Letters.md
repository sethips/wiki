# Algorithm Missing Letters

:triangular_flag_on_post: Remember to use [**`Read-Search-Ask`**](FreeCodeCamp-Get-Help) if you get stuck. Try to pair program :busts_in_silhouette: and write your own code :pencil:

### :checkered_flag: Problem Explanation:

You will create a program that will find the missing letter from a string and add it. If there is no missing letter, the program should return undefined. There is currently no test case for the string missing more than one letter, but if there was one, recursion would be used. Also, the letters are always provided in order so there is no need to sort them.

#### Relevant Links

- [String global object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
- [JS String Prototype CharCodeAt](JS-String-Prototype-CharCodeAt)
- [String.fromCharCode](String.fromCharCode)

## :speech_balloon: Hint: 1

You will need to convert from character to ASCII code using the two methods provided in the description.

> _try to solve the problem now_

## :speech_balloon: Hint: 2

You will have to check for the difference in ASCII code as they are in order. Using a chart would be very helpful.

> _try to solve the problem now_

## :speech_balloon: Hint: 3

You will need to figure out where to insert the letter and how to do it, along with handling the case that there is not missing letter as it needs an specific return value.

> _try to solve the problem now_

## Spoiler Alert!

![687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif](https://files.gitter.im/FreeCodeCamp/Wiki/nlOm/thumb/687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif)

**Solution ahead!**

## :beginner: Basic Code Solution:

```javascript
function fearNotLetter(str) {

  for(var i = 0; i < str.length; i++) {
    /* code of current character */
    var code = str.charCodeAt(i);

    /* if code of current character is not equal to first character + no of iteration
    hence character has been escaped */
    if (code !== str.charCodeAt(0) + i) {

      /* if current character has escaped one character find previous char and return */
      return String.fromCharCode(code - 1);
    }  
  }
  return undefined;
}

// test here
fearNotLetter("abce");
```

:rocket: [Run Code](https://repl.it/CLnD/0)

### Code Explanation:

- This solutions makes use of a `for` loop.
- Code of encountered character is stored in **code**.
- It is checked if code of current character is the expected one (no characters are skipped) by using the logic - `code of current character = code of first character + number of iterations`.
- If a character is missing, the missing character is found and the final string is returned.
- `undefined` is returned if there is no missing character in the string.

#### Relevant Links

- [JS For Loops Explained](JS-For-Loops-Explained)
- [String.length](String.length)

## :sunflower: Intermediate Code Solution:

```javascript
// Adding this solution for the sake of avoiding using 'for' and 'while' loops.
// See the explanation for reference as to why. It's worth the effort.

function fearNotLetter(str) {
  var compare = str.charCodeAt(0), missing;

  str.split('').map(function(letter,index) {
    if (str.charCodeAt(index) == compare) {
      ++compare;
    } else {
      missing = String.fromCharCode(compare);
    }
  });

  return missing;
}

// test here
fearNotLetter("abce");
```

:rocket: [Run Code](https://repl.it/CLnE/0)

### Code Explanation:

- First we define variables to store the character code for the first letter in the string, and to store whatever missing letters we may find.
- We turn the string to an array in order to map through it instead of using `for` and `while` loops.
- As we `map` through our letters' character codes, we go comparing with the one that should be in that position.
- If the current letter matches, we move the comparison variable to its next position so we can compare on the next cycle.
- If not, the missing letter will be assigned to the `missing` variable, which will be returned after the map is finished.
- If there are no missing characters, return `undefined`.

#### Relevant Links

- [JS String Prototype Split](JS-String-Prototype-Split)
- [JS Array Prototype Map](JS-Array-Prototype-Map)

## :rotating_light: Advanced Code Solution:

```javascript
function fearNotLetter(str) {
  var allChars = '';
  var notChars = new RegExp('[^'+str+']','g');

  for (var i = 0; allChars[allChars.length-1] !== str[str.length-1] ; i++)
    allChars += String.fromCharCode(str[0].charCodeAt(0) + i);

  return allChars.match(notChars) ? allChars.match(notChars).join('') : undefined;
}

// test here
fearNotLetter("abce");
```

:rocket: [Run Code](https://repl.it/CLnG/0)

### Code Explanation:

- A new string **allChars** is created.
- Create a regular expression **notChars** which selects everything except **str**.
- The `for` loop is used to add all the letters in the range to **allChars**.
- `match()` is used to strip off the **str** letters from the newly created string and it is returned.
- If there are no missing characters, return `undefined`.

#### Relevant Links

- [JS Regex Resources](JS-Regex-Resources)
- [JS Ternary](JS-Ternary)
- [JS String Prototype Match](JS-String-Prototype-Match)
- [JS Array Prototype Join](JS-Array-Prototype-Join)

### :trophy: Credits:

If you found this page useful, you may say thanks to the contributors by copying and pasting the following line in the main chat:

**`Thanks @Rafase282 @rohitnwn @sabahang @Hallaathrad  for your help with Algorithm: Missing Letters`**

## :clipboard: NOTES FOR CONTRIBUTIONS:

- :warning: **DO NOT** add solutions that are similar to any existing solutions. If you think it is **_similar but better_**, then try to merge (or replace) the existing similar solution.
- Add an explanation of your solution.
- Categorize the solution in one of the following categories &mdash; **Basic**, **Intermediate** and **Advanced**. :traffic_light:
- Please add your username only if you have added any **relevant main contents**. (:warning: **_DO NOT_** _remove any existing usernames_)

> See :point_right: [**`Wiki Challenge Solution Template`**](Wiki-Template-Challenge-Solution) for reference.
