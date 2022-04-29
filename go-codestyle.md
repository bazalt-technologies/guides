# Go Codestyle Standard bazalt 0.2

## Chapter 1. Project Structure
Root of the project should have as little as possible directories/packages.  
In a perfect case root should contain the structure of two packages:  
one containing executable files and one containing helping functions/methods/structures/interfaces split by packages.  
The aim of this requirement is to increase readability of program source code.  

## Chapter 2. Naming
### General Rules

All the variables, functions, methods etc. should be named in CamelCase practice.   
If name starts with an uppercase letter, function will be available to import from other packages.  
If name starts with a lowercase letter, other packages will not be able to import it.
Do not name variables, functions, methods etc. with a repeating or reminding names

**Don't:**
```
var foo_bar int
var foobar int
func FooBar int {
	var foobar, fooBar, foo int
```
**Do:**
```
var foo int
var Bar int
```
### Structures and Interfaces
Structures should have a noun as a name according to what they mean.  
Interfaces have to be named with a noun according to functions they represent with a suffix -er.  


**Don't:**
```
type SayDate struct {
	date time.Time
	format int
}
type Say interface {
	Print()
}
```
**Do:**
```
type Date struct {
	date time.Time
	format int
}
```
### Functions
Functions should not take more than five arguments  
Functions should not be called with suffix -er  

## Chapter 3. Code
### Comments
Every comment starts with `\\` sign and have a space after it.  

All comments should be in English  

All the functions should have comment before they defined.  
According to Go standards, function's comment should have name of function in it.  

Variables (unless they are temporary or their usage is obvious) should be commented when initialised.  
*Try to name them so that comments were not necessary.*
Important variables that are used all over the function should be initialised in the beginning of a function and commented on the right aligned on right.  
Other variables should be commented in the line before.  
Variables initialised with `:=` sign have to be commented  

Within a function, any complex piece of code should have a comment explaining what is going on.  
It should be one line before the piece of code and have an extra empty line.  

**Don't:**
```
func GreatestCommonDivisor(aOriginal, bOriginal Polynomial) Polynomial {
var GCD Polynomial //Наибольший общий делитель
var nominator, denominator natural.Natural //Множитель и делитель для…
var multiplier rational.Rational //Множитель для полученного…
//Применяем алгоритм Евклида
for !((a.Older == 0 && rational.Compare(a.Coeff[0], rational.Zero()) == 0) ||
. . .
```
**Do:**
```
// GreatestCommonDivisor Finds GCD of two given polynomials 
func GreatestCommonDivisor(aOriginal, bOriginal Polynomial) Polynomial {
var GCD Polynomial                         // Greatest Common Divisor
var nominator, denominator natural.Natural // Factor and Divisor…
var multiplier rational.Rational           // Factor for…

// Using Euclid`s algorythm
for !((a.Older == 0 && rational.Compare(a.Coeff[0], rational.Zero()) == 0) ||
. . .
```
### If . . . else if . . . else
Try avoiding chains of if else statements if there is more than one condition.  
Use switch cases or returns instead.
