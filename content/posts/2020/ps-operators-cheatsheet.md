+++
date = '2020-06-01T20:10:26-06:00'
draft = false
title = 'PowerShell Compare Operators Cheatsheet'
type = 'post'
tags = ["tech", "devops", "enterprise-it", "cheatsheet", "powershell", "beginner-fundamentals"]
+++
# Comparison Operators

The following operators are all Case-Insensitive by default:

- `-eq` Equal
- `-ne` Not equal
- `-ge` Greater than or equal
- `-gt` Greater than
- `-lt` Less than
- `-le` Less than or equal
- `-like` Wildcard comparison
- `-notlike` Wildcard comparison
- `-match` Regular expression comparison
- `-notmatch` Regular expression comparison
- `-replace` Replace operator
- `-contains` Containment operator
- `-notcontains` Containment operator
- `-in` Like –contains, but with the operands reversed.(PowerShell 3.0)
- `-notin` Like –notcontains, but with the operands reversed.(PowerShell 3.0)

To perform a Case-Sensitive comparison just prefix any of the above with "c" for example `-ceq` for case-sensitive Equals or `-creplace` for case-sensitive replace.

Similarly prefixing with "i" will explicitly make the operator explicitly case insensitive. It seems likely that these short names such as `-eq` were chosen for operators instead of symbols (= / <> etc) to allow for these case sensitive options.

## Types

- `-is` Is of a type
- `-isnot` Is not of a type
- `-as` As a type, no error if conversion fails

## Logical operators

- `-and` Logical And
- `-or` Logical Or
- `-xor` Logical exclusive Or
- `-not` logical not
- `!` logical not

## Bitwise operators 

- `-band` Bitwise and
- `-bor` Bitwise or
- `-bXor` Bitwise OR (exclusive)
- `-bNot` Bitwise NOT
- `-shl` Shift bits left (PowerShell 3.0)
- `-shr` Shift bits right – preserves sign for signed values.(PowerShell 3.0)

## Format Operator

`"format_string" -f Object1, Object2,...`

The format_string is in the form: `{0,-5} {1,-20} {2,-10}`

In each set of braces, the first number, before the comma refers to the column. The second number, after the comma determines the padding (how many characters) If the second number is negative, it not only pads the element, but aligns it vertically. Optionally the second number can be used for formatting :hh :mm :C :p

When applied to an array, comparison operators will work as a filter returning all the values which match.

## Filters

A PowerShell Filter will accept the following operators

- `-eq`
- `-ne`
- `-ge`
- `-gt`
- `-lt`
- `-le`
- `-like`
- `-notlike`
- `-approx`
- `-bor`
- `-band`
- `-recursivematch`

Notice that this list misses out several useful operators such as `-match` and `-contains` but those can still be used by piping to a Where-Object clause: `... | Where {$_.name –match 'value'}`

## Examples

```powershell
$demo = $null
if (-Not ($demo)) { write "Zero, null or Empty"}
if (!($demo)) { write "Zero, null or Empty"}

$myVar -is "String"
$myVar -eq 123 
$myVar -ceq $myVar2 
"abcdef" -like "abc*"
"abcdef" -replace "dEf","xyz"
$myVar1 -is "String" -and $myVar2 -is "Int"
"{2:N}" -f 24.4567
(1 -eq 1) -and -not (2 -gt 2) 

$mycmd = ps | select id,ProcessName
foreach ($proc in $mycmd) {"{0,-8}{1,-20}" -f $proc.id, $proc.ProcessName}
```

Related PowerShell Cmdlets:

- if - Conditionally perform a command.
- Assignment Operators ( $variable = X, $variable += Y )
- PowerShell Regular Expressions
- Format-Table
