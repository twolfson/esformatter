# Comprehensive list of options
This document aims to document/provide examples of each option.

## Notes
// TODO: Break down into `whitespace`, `linebreak`, and `indent` sections

## Whitespace
Each of the following is a valid key for both whitespace `before` and `after` unless noted otherwise.

// Nodes
// https://github.com/facebook/esprima/blob/4001.1001.0000-dev-harmony-fb/esprima.js#L127-L203
ArrayExpression
ArrayPattern
ArrowFunctionExpression
AssignmentExpression
BinaryExpression
BlockStatement
BreakStatement
CallExpression
CatchClause
ClassBody
ClassDeclaration
ClassExpression
ComprehensionBlock
ComprehensionExpression
ConditionalExpression
ContinueStatement
DebuggerStatement
DoWhileStatement
EmptyStatement
ExportDeclaration
ExportBatchSpecifier
ExportSpecifier
ExpressionStatement
ForInStatement
ForOfStatement
ForStatement
FunctionDeclaration
FunctionExpression
Identifier
IfStatement
ImportDeclaration
ImportSpecifier
LabeledStatement
Literal
LogicalExpression
MemberExpression
MethodDefinition
ModuleDeclaration
NewExpression
ObjectExpression
ObjectPattern
Program
Property
ReturnStatement
SequenceExpression
SpreadElement
SpreadProperty
SwitchCase
SwitchStatement
TaggedTemplateExpression
TemplateElement
TemplateLiteral
ThisExpression
ThrowStatement
TryStatement
TypeAnnotatedIdentifier
TypeAnnotation
UnaryExpression
UpdateExpression
VariableDeclaration
VariableDeclarator
WhileStatement
WithStatement
XJSIdentifier
XJSNamespacedName
XJSMemberExpression
XJSEmptyExpression
XJSExpressionContainer
XJSElement
XJSClosingElement
XJSOpeningElement
XJSAttribute
XJSSpreadAttribute
XJSText
YieldExpression

// TODO: Do we present access to these outside? How is `processComment` handled?
// Tokens
https://github.com/facebook/esprima/blob/4001.1001.0000-dev-harmony-fb/esprima.js#L104-L114
Boolean
<end>
Identifier
Keyword
Null
Numeric
Punctuator
String
XJSIdentifier
XJSText
RegularExpression

### esformatter.js
  // Effectively all esprima nodes
  function transformNode(node) {
    _ws.limitBefore(node.startToken, node.type);
    _ws.limitAfter(node.endToken, node.type);

  // Comments
  function processComment(token) {
    _ws.limitBefore(token, token.type);
    // only block comment needs space afterwards
    if (token.type === 'BlockComment') {
      _ws.limitAfter(token, token.type);
    }
  }
  .type === .type ===
    if (token.type === 'BlockComment') {
    if (token.type === 'BlockComment') {
    if (token.type === 'BlockComment') {
    if (token.type === 'BlockComment') {


  expressionParentheses.addSpaceInside(node);
  // see "expression parentheses"

  // brs
  function transform(ast, opts) {
    _br.limitBeforeEndOfFile(ast);

  function preprocessToken(token) {
    if (_tk.isComment(token)) {
      _br.limit(token, token.type);
    }

  addBrAroundNode(node);
  Top level sooo basically everything
    _br.limitBefore(node.startToken, type);

    if (_tk.isSemiColon(node.endToken)) {
      _br.limitAfter(node.endToken, type);
    }

  // All esprima nodes
  function getIndentLevel(node) {
    var value = _opts[node.type];

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
  _limit.before(firstArg.startToken, getArgumentType(firstArg));
    ArrayExpression: true,
    FunctionExpression: true,
    ObjectExpression: true

  _limit.around(next, 'ArgumentComma');
  _limit.after(lastArg.endToken, getArgumentType(lastArg));
    ArrayExpression: true,
    FunctionExpression: true,
    ObjectExpression: true

### catch clause
  _limit.around(node.startToken, 'CatchKeyword');

  _limit.before(node.param.startToken, 'CatchParameterList');
  _limit.after(node.param.endToken, 'CatchParameterList');

  _limit.around(node.body.startToken, 'CatchOpeningBrace');
  _limit.around(node.body.endToken, 'CatchClosingBrace');

### conditional expression
  _ws.limitBefore(questionMark, _ws.getAmountAfterType('ConditionalExpressionTest'));
  _ws.limitAfter(questionMark, _ws.getAmountBeforeType('ConditionalExpressionConsequent'));
  _ws.limitBefore(colon, _ws.getAmountAfterType('ConditionalExpressionConsequent'));
  _ws.limitAfter(colon, _ws.getAmountBeforeType('ConditionalExpressionAlternate'));

### do while statement
  _br.limit(node.body.startToken, 'DoWhileStatementOpeningBrace');
  _ws.limit(node.body.startToken, 'DoWhileStatementOpeningBrace');
  _br.limit(node.body.endToken, 'DoWhileStatementClosingBrace');
  _ws.limit(node.body.endToken, 'DoWhileStatementClosingBrace');

### for in statement

  _br.limit(expressionStart, 'ForInStatementExpressionOpening');
  _ws.limit(expressionStart, 'ForInStatementExpressionOpening');

  _br.limit(expressionEnd, 'ForInStatementExpressionClosing');
  _ws.limit(expressionEnd, 'ForInStatementExpressionClosing');

  _br.limit(bodyStart, 'ForInStatementOpeningBrace');
  _ws.limit(bodyStart, 'ForInStatementOpeningBrace');

  _br.limit(bodyEnd, 'ForInStatementClosingBrace');
  _ws.limit(bodyEnd, 'ForInStatementClosingBrace');

  _ws.limitAfter(expressionEnd, 'ForInStatementExpression');

### for statement
  _limit.around(expressionStart, 'ForStatementExpressionOpening');
  _limit.around(expressionEnd, 'ForStatementExpressionClosing');
  if (semi_1) _ws.limit(semi_1, 'ForStatementSemicolon');
  if (semi_2) _ws.limit(semi_2, 'ForStatementSemicolon');
  _limit.around(bodyStart, 'ForStatementOpeningBrace');
  _limit.around(bodyEnd, 'ForStatementClosingBrace');

### function declaration
  _limit.after(node.id.startToken, 'FunctionName');
  _params.format(node);
  _limit.around(node.body.startToken, 'FunctionDeclarationOpeningBrace');
  _limit.around(node.body.endToken, 'FunctionDeclarationClosingBrace');

  _params.format(node);
  // via ../params.js
    _ws.limitBefore(params[0].startToken, 'ParameterList');
        _ws.limit(_tk.findNext(param.startToken, ','), 'ParameterComma');
    _ws.limitAfter(params[params.length - 1].endToken, 'ParameterList');

### function expression
  if (node.id) {
    _ws.limitAfter(node.id.startToken, 'FunctionName');
  } else {
    _ws.limit(node.startToken, 'FunctionReservedWord');
  }

  _params.format(node);
  // via ../params.js
    _ws.limitBefore(params[0].startToken, 'ParameterList');
        _ws.limit(_tk.findNext(param.startToken, ','), 'ParameterComma');
    _ws.limitAfter(params[params.length - 1].endToken, 'ParameterList');

### if statement
  _ws.limit(conditionalStart, 'IfStatementConditionalOpening');
  _ws.limit(conditionalEnd, 'IfStatementConditionalClosing');
  _br.limitBefore(alt.consequent.startToken, 'ElseIfStatementOpeningBrace');
  _br.limitBefore(alt.consequent.endToken, 'ElseIfStatementClosingBrace');
  _br.limitBefore(elseKeyword, 'ElseIfStatement');
  _br.limitAfter(alt.consequent.endToken, 'ElseIfStatement');

  _limit.around(alt.startToken, 'ElseStatementOpeningBrace');

  _br.limitBefore(elseKeyword, 'ElseStatement');
  _br.limitAfter(alt.endToken, 'ElseStatement');

  _limit.around(alt.endToken, 'ElseStatementClosingBrace');

  _limit.around(startBody, 'IfStatementOpeningBrace');
  if (!alt) {
    _br.limit(endBody, 'IfStatementClosingBrace');
  } else {
    _br.limitBefore(endBody, 'IfStatementClosingBrace');
  }
  _ws.limit(endBody, 'IfStatementClosingBrace');


### logical expression
  _ws.limit(operator, 'LogicalExpressionOperator');
  _br.limit(prev, 'ExpressionOpeningParentheses');
  _ws.limit(prev, 'ExpressionOpeningParentheses');
  _br.limit(next, 'ExpressionClosingParentheses');
  _ws.limit(next, 'ExpressionClosingParentheses');

### member expression
  if (opening && closing && opening.value === '[' && closing.value === ']') {
    _ws.limitAfter(opening, "MemberExpressionOpening");
    _ws.limitBefore(closing, "MemberExpressionClosing");
  }

### object expression
  var shouldBeSingleLine = node.parent.type === 'ForInStatement';

  if (!shouldBeSingleLine) {
    _limit.around(node.startToken, 'ObjectExpressionOpeningBrace');
  } else {

  // ...

  if (!shouldBeSingleLine) {
    _br.limitBefore(prop.key.startToken, 'PropertyName');
    _br.limitAfter(prop.key.endToken, 'PropertyName');
    _br.limitBefore(prop.value.startToken, 'PropertyValue');
    _br.limitAfter(prop.value.endToken, 'PropertyValue');
  } else if (prop.key.startToken.prev.value !== '{') {
    _ws.limitBefore(prop.key.startToken, 'Property');
  }

  _ws.limitBefore(prop.key.startToken, 'PropertyName');
  _ws.limitAfter(prop.key.endToken, 'PropertyName');
  _ws.limitBefore(valueStart, 'PropertyValue');
  _ws.limitAfter(valueEnd, 'PropertyValue');

  // ...

  if (!shouldBeSingleLine) {
    _limit.around(node.endToken, 'ObjectExpressionClosingBrace');
  }

### params
    _ws.limitBefore(params[0].startToken, 'ParameterList');
      _ws.limit(_tk.findNext(param.startToken, ','), 'ParameterComma');
    _ws.limitAfter(params[params.length - 1].endToken, 'ParameterList');

### return statement
    expressionParentheses.addSpaceInside(node.argument);
    // see "expression parentheses"

### sequence expression
nothing

### switch case
  _limit.around(openingBrace, 'SwitchOpeningBrace');
  _limit.around(closingBrace, 'SwitchClosingBrace');
  _limit.around(opening, 'SwitchDiscriminantOpening');
  _limit.around(closing, 'SwitchDiscriminantClosing');

### throw statement
  _ws.limit(node.startToken, 'ThrowKeyword');

### try statement
  _limit.around(finallyKeyword, 'FinallyKeyword');
  _limit.around(finalizer.startToken, 'FinallyOpeningBrace');
  _limit.around(finalizer.endToken, 'FinallyClosingBrace');

  // CatchClause is handled by its own hook

  _limit.around(node.startToken, 'TryKeyword');
  _limit.around(node.block.startToken, 'TryOpeningBrace');
  _limit.around(node.block.endToken, 'TryClosingBrace');

### unary expression
  _br.limitBefore(node.startToken, 'DeleteOperator');
  _br.limitAfter(endToken, 'DeleteOperator');
  _ws.limit(node.startToken, 'UnaryExpressionOperator');

### update expression
nothing

### variable delcaration
  _br.limit(idStartToken, 'VariableName');
  _ws.limitBefore(idStartToken, 'VariableName');
  _ws.limitAfter(declarator.id.endToken, 'VariableName');
  _ws.limitAfter(declarator.id.endToken, 'VariableName');
  _br.limitBefore(valueStart, 'VariableValue');
  _ws.limitBefore(valueStart, 'VariableValue');
  _br.limitAfter(declarator.endToken, 'VariableValue');
  _ws.limitAfter(declarator.endToken, 'VariableValue');

### while statement
  _limit.around(conditionalStart, 'WhileStatementConditionalOpening');
  _limit.around(bodyStart, 'WhileStatementOpeningBrace');
  _limit.around(bodyEnd, 'WhileStatementClosingBrace');
  _limit.around(conditionalEnd, 'WhileStatementConditionalClosing');
  _limit.before(conditionalEnd, 'WhileStatementConditionalClosing');
  _limit.after(conditionalEnd, 'WhileStatementConditionalClosing');

### expression parentheses
  _ws.limitAfter(parentheses.opening, 'ExpressionOpeningParentheses');
  _ws.limitBefore(parentheses.closing, 'ExpressionClosingParentheses');
