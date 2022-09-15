# Part 1: Making a GET Request

## In this exercise, we’re going to apply that code to access the [Datamuse API](https://www.datamuse.com/api/) and render the fetched information in the browser.

The Datamuse API is a word-finding query engine for developers. It can be used in apps to find words that match a given set of constraints that are likely in a given context.

If the request is successful, we’ll get back an array of words that sound like the word we typed into the input field.

## Instructions

- 1. At the top of **main.js**, create a `const` variable called `url`. Assign `url` to the following URL as a string:

  ```
  // Information to reach API
  const url = "https://api.datamuse.com/words?sl=";
  ```

  The `?sl=` portion of the string will be the start of your [query string](https://en.wikipedia.org/wiki/Query_string), which will be used to pass parameters to the Datamuse API. The query string will be used by the engine to narrow the search to words that sound like your word.

- 2. Inside the `getSuggestions()` function, create a `const` variable called `wordQuery` and assign it `inputField.value`.

  We’ll need `wordQuery` to store the value of what is being typed into the input field.

  Create another `const` variable called `endpoint` and assign it the value of a string that is `url`, and `wordQuery` concatenated in that order.

  We will be working inside `getSuggestions()` function for the remainder of this exercise.

- 3. Inside the `getSuggestions()` function, call the `fetch()` function and pass in `endpoint` as an argument. For this API to work within the Codecademy browser, add `{cache: 'no-cache'}` as the second argument.

## Part 2

- 1. At the end of the `.then()` method, chain another `.then()` method.

As the first argument of our second `.then()` method, pass an anonymous arrow callback function that takes `jsonResponse` as its single parameter.

- 2. Inside the callback function we just created, call the `renderRawResponse()` function and pass in `jsonResponse` as its argument. Run the code.

In the input field, type in a word and click the submit button.

If all went well, we should see an array of words that the Datamuse API responded with!

Note that you can find the `renderRawResponse()` function declaration in **public/helperFunctions.js**.

- 3. Let’s format our response from the Datamuse API to look presentable on the webpage. To do this, we will use the `renderResponse()` function that’s been defined in **public/helperFunctions.js**.

Comment out `renderRawResponse(jsonResponse)`. Then below, call `renderResponse(jsonResponse)`.

Run your code.

Try the webpage again with another word!

# Part 2: Making an async GET Request

```
// Information to reach API
const url = "https://api.datamuse.com/words?";
const queryParams = "rel_jja=";
```

- 1. Inside the `getSuggestions()` function, create a `const` variable named `wordQuery` and assign it inputField.value.

- 2. Create another `const` variable called `endpoint` and assign it the value of a string that is `url`, `queryParams`, and `wordQuery` concatenated in that order.

- 3. Add a `try` statement with an empty code block. Outside the code block for try, add a `catch(error)` statement with a code block that logs `error` to the console.

- 4. Inside the `try` code block, create a `const` variable named `response` and assign it to `await` the result of calling `fetch()` with `endpoint` as the first argument. For this API to work within the Codecademy browser, add `{cache: 'no-cache'}` as the second argument.

- 5. Below the response variable declaration from the previous step, create a conditional statement that the checks if the `ok` property of the `response` evaluates to a truthy value.

  Inside the code block of the conditional statement, `await` `response.json()` and save it to a new `const` variable called `jsonResponse`

- 6. Still inside the conditional statement, call the function `renderResponse()` and pass in `jsonResponse`. Then, run the code.

  In the input field, type in a word and click the submit button on the web page.

  Great, now we have an organized list of words from the GET request!
