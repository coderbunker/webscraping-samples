# webscraping-samples
To explore how to do web scraping


## Overview

This exercise shows extraction of keywords from a webpage using Javascript.

## Steps

This is an example of code, implemented on the chrome DevTools. The page is https://forums.macrumors.com/forums/macrumors-com-news-discussion.4/ 

To start off, figure out the tag element of the list to be extrated. Here, the list of titles on the page is stored in <h3>

```javascript
document.getElementsByTagName('h3')   // extract the list of the title by TagName
```

```javascript
typeof document.getElementsByTagName('h3')   // check the type of the <h3>
```

```javascript
allHeadings = document.getElementsByTagName('h3')   // store the objects in the allHeadings variable
```

```javascript
allHeadings_list = Array.prototype.slice.call(allHeadings)   // create an array allHeadings_list
```

```javascript
titles = allHeadings_list.map(e => e.innerText)   // extract the text from the <h3> element as titles
```

```javascript
//Using .map() to create new array of every element in keywords. In the every new array, the elements are split by space '' 
keywords = titles.map(t => t.split(' '))   

//check keywords[0] to see the result 
keywords[0]
```

```javascript
words = [].concat.apply([], keywords)  
words.sort()
// concatenate the keywords, store it in words, and sort by alphabet
```

```javascript
// define onlyUnique function to extract the unique value from the array
function onlyUnique(value, index, self) { 
    return self.indexOf(value) === index;
}

// extract the unique values from words 
uniqueWords = words.filter(onlyUnique)
```

Next I want to filter out the stopwords to get the meaningful keywords

```javascript
// import a list of stopwords as a new variable 
var stopwords = [
  'about', 'after', 'all', 'also', 'am', 'an', 'and', 'another', 'any', 'are', 'as', 'at', 'be',
  'because', 'been', 'before', 'being', 'between', 'both', 'but', 'by', 'came', 'can',
  'come', 'could', 'did', 'do', 'each', 'for', 'from', 'get', 'got', 'has', 'had',
  'he', 'have', 'her', 'here', 'him', 'himself', 'his', 'how', 'if', 'in', 'into',
  'is', 'it', 'like', 'make', 'many', 'me', 'might', 'more', 'most', 'much', 'must',
  'my', 'never', 'now', 'of', 'on', 'only', 'or', 'other', 'our', 'out', 'over',
  'said', 'same', 'see', 'should', 'since', 'some', 'still', 'such', 'take', 'than',
  'that', 'the', 'their', 'them', 'then', 'there', 'these', 'they', 'this', 'those',
  'through', 'to', 'too', 'under', 'up', 'very', 'was', 'way', 'we', 'well', 'were',
  'what', 'where', 'which', 'while', 'who', 'with', 'would', 'you', 'your', 'a', 'i']
```

```javascript
keywords_list = uniqueWords.filter(w => stopwords.indexOf(w) < 0)   // Get the final list of keywords without stopwords
```








