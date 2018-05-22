# Sapphire
language of cherry picked functional & objective.

# Document definition
syntax is wrote in [ABNF](https://en.wikipedia.org/wiki/Augmented_Backus–Naur_form)

## predefined rule
### ABNF core rules
```ABNF
<ALPHA> = %x41-5A / %x61-7A ; alphabets [a-zA-Z]
<DIGIT> = %x30-39 ; digit [0-9]
<HEXDIG> = DIGIT / "A" / "B" / "C" / "D" / "E" / "F" ; [0-9a-fA-F]
<DQUOTE> = %x22 ; double quote
<SP> = %x20 ; space
<HTAB> = %x09 ; tab
<WSP> = <SP> / <HTAB>
<LWSP> = *(<WSP> / <CRLF> <WSP>)
<VCHAR> = %x21-7E ; printable characters
<CHAR> = %x01-7F ; ascii characters without NUL
<OCTET> = %x00-FF ; 8bit data
<CTL> = %x00-1F / %x7F ; control characters
<CR> = %x0D
<LF> = %x0A
<CRLF> = <CR> <LF>
<BIT> = "0" / "1"
```

### implement rule
```ABNF
<implement>
```

### util rules
```ABNF
<eol> = <CRLF> / <CR> / <LF>
<unicode-char> = <implement> ; implement unicode characters (without control character, but included WSP)
```

# Outline

* [Lexical elements](#Lexical-elements)
    * [identify](#identify)
    * [comments](#comments)
    * [reserved keywords](#reserved-keywords)
    * [operators](#operators)
        * [unary operators](#unary-operatos)
        * [binary operators](#binary-operators)
        * [ternary operator](#ternary-operator)
        * [assignment operators](#assignment-operators)
        * [access operators](#access-operators)
        * [call operator](#call-operator)

# Lexical elements

## identify
### syntax
```ABNF
<identify> = <ALPHA> *(<ALPHA> / <DIGIT> / "_")
```

## comments
### syntax
```ABNF
<comments> = <line-comment> / <block-comment>
<line-comment> = "//" *(<unicode-char> <eol>)
<block-comment> = "/*" *(<unicode-char> <eol>) "*/"
```
### example
```
// line comment
/*block comment*/
```
## reserved keywords
```ABNF
<keyword> = <implement> ; anyword of follow contents
```

> reserved keywords contains not used for compatibility of other languages (ex. c/c++).

```
alias
align
array
asm
async
assert
auto

bool
break
byte

case
cast
catch
char
class
compiled
const
continue

default
delegate
delete
deprecated
do
double

else
enum
export
extern

false
final
float
for
foreach
function

goto

if
immutable
import
in
inout
int
interface
is

lazy
long
local

macro
module

new
nothrow
null

out
override

package
pragma
private
protected
public

ref
return
scope
shared
short
static
string
struct
switch
sync

template
this
throw
true
try
type
typeid
typeof

ubyte
uint
ulong
unicode
union
unit
ushort
ustring

while
with

__file_path__
__file_name__
__function__
__line__
```

## operators
### unary operators
```ABNF
<unary-operators> = "++" / "--" / "**" / "!" / "^"
```
### binary operators
```ABNF
<binary-operators> = "+" / "-" / "*" / "/" / "&" / "&&" / "|" / "||" / ">>" / "<<" / "|>" / "%"
```

### ternary operator
exist only **?:**

### syntax
```
<sentence> "?" <sentence> ":" <sentence>
```

### assignment operators
```ABNF
<assignment-operators> = "+=" / "-=" / "*=" / "/=" / "|=" / "&=" / "%="
```

### access operators
```
[]
*
&
.
->
.?
```

### call operator
```
()
```


## literals


## variable