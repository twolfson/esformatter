# Comprehensive list of options
This document aims to document/provide examples of each option.

## Notes
// TODO: Break down into `whitespace` and `linebreak` sections
// TODO: Grab any non-hooks `_ws` or `_br` calls

### hooks/ArrayExpression.js
```js
_limit.around(node.startToken, 'ArrayExpressionOpening');
_limit.around(node.endToken, 'ArrayExpressionClosing');
_limit.around(prev, 'ArrayExpressionComma');
```

### hooks/AssignmentExpression.js
```js
_br.limit(operator, 'AssignmentOperator');
_ws.limit(operator, 'AssignmentOperator');
```

### binary expression
  _ws.limit(operator, 'BinaryExpressionOperator');

### call expression
TODO

### catch clause
TODO

### conditional expression
TODO

### do while statement
TODO

### for in statement
TODO

### for statement
TODO

### function declaration
TODO

### function expression
TODO

### if statement
TODO

### logical expression
TODO

### member expression
TODO

### object expression
TODO

### params
    _ws.limitBefore(params[0].startToken, 'ParameterList');
      _ws.limit(_tk.findNext(param.startToken, ','), 'ParameterComma');
    _ws.limitAfter(params[params.length - 1].endToken, 'ParameterList');


### return statement
nothing

### sequence expression
TODO

### switch case
TODO

### throw statement
TODO

### try statement
TODO

### unary expression
TODO

### update expression
TODO

### variable delcaration
TODO

### while statement
TODO

### expression parentheses
TODO
