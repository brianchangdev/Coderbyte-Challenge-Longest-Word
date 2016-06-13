# Coderbyte-Challenge-Longest-Word
Have the function LongestWord(sen) take the sen parameter being passed and return the largest word in the string. If there are two or more words that are the same length, return the first word from the string with that length. Ignore punctuation and assume sen will not be empty. 

MY SOLUTION: Passed some cases, failed the following
1. When the input was "a beautiful sentence^&!" your output was incorrect.
2. When the input was "letter after letter!!" your output was incorrect.
3. When the input was "a confusing /:sentence:/[ this is not!!!!!!!~" your output was incorrect.

    function LongestWord(sen) { 
    var biggestWord = '';
    var words = sen.split(' ');
    words.forEach(function(word){
       if(word.length > biggestWord.length ){
           biggestWord = word
       }
    });
    return biggestWord; 
    }
    
Best solution: 
    
      function longestWord(sen){
    // regex is used to form search pattern and then .replace() to replace those characters in sentence
    // First paramater of replace is to search
    // [^A-Za-z] means any character that IS NOT a-z OR A-Z
    // /g means find all matches
    // second param is what to replace it with "" or empty space, in other words ignore those special characters
    
      var words = sen.replace(/[^A-Za-z\s]/g, "").split(" ");
      var wordsByDescendingLength = words.sort(function(a, b) {
      // b.length - a.length sort each word by length in descending order. The first entry in the array is the longest word
        return b.length - a.length;
        });
        // call the first word in array [0] which is the longest
        return wordsByDescendingLength[0];
