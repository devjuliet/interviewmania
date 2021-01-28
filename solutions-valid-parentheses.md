```javascript
//Excellent
function validParentheses(parens) {
    let n = 0;
    for (let i = 0; i < parens.length; i++) {
        if (parens[i] == "(") n++;
        if (parens[i] == ")") n--;
        if (n < 0) return false;
    }
    return n == 0;
}

Test.assertEquals(validParentheses("()"), true);
Test.assertEquals(validParentheses("())"), false);

//Good
function validParentheses(parens) {
    let stack = 0;

    for (let i = 0; i < parens.length && stack >= 0; i++) {
        stack += parens[i] == "(" ? 1 : -1;
    }

    return stack == 0;
}

// Mixed (how would you do it without an array?)
function validParentheses(parens) {
    let stack = [];

    for (let i = 0; i < parens.length; i++) {
        if (parens[i] === "(") {
            stack.push(parens[i]);
        } else if ("(" !== stack.pop()) {
            return false;
        }
    }

    return stack.length === 0;
}
```
