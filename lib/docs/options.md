# Comprehensive list of options
This document aims to document/provide examples of each option.

## Notes
// TODO: Break down into `whitespace` and `linebreak` sections
### ArrayExpression.js

_limit.around(node.startToken, 'ArrayExpressionOpening');
_limit.around(node.endToken, 'ArrayExpressionClosing');
_limit.around(prev, 'ArrayExpressionComma');
