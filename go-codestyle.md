# Go Codestyle Standard bazalt 0.2.1

## Chapter 1. Project Structure
1.1. Root of the project should have as little as possible directories/packages.  
     In a perfect case root should contain the structure of two packages:  
     - one containing executable files
     - one containing helping functions/methods/structures/interfaces split by packages.  

*The aim of this requirement is to increase readability of program source code.*  

## Chapter 2. Naming
### 2.1. General Rules

2.1.1. All the variables, functions, methods etc. should be named in CamelCase practice.   
2.1.2. If name starts with an uppercase letter, function will be available to import from other packages.  
2.1.3. If name starts with a lowercase letter, other packages will not be able to import it.
2.1.4. Do not name variables, functions, methods etc. with a repeating or reminding names

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
### 2.2. Structures and Interfaces
2.2.1. Structures should have a noun as a name according to what they mean.  
2.2.2. Interfaces have to be named with a noun according to functions they represent with a suffix -er.  


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
### 2.3. Functions
2.3.1. Functions should not take more than five arguments  
2.3.2. Functions should not be called with suffix -er  

## Chapter 3. Code
### 3.1. Comments
3.1.1. All the comments should start with `\\` sign and have a space after it.  
3.1.2. All the comments should be one line before the piece of code it explains.  
3.1.3. All the comments should be in English  

3.1.4. All the functions should have comment before they defined.  
  *According to Go standards, function's comment should have name of function in it.*  

3.1.5. Variables (unless they are temporary or their usage is obvious) should be commented when initialised.  
*Try to name them so that comments were not necessary.*
3.1.6. Important variables that are used all over the function should be initialised in the beginning of a function.    
3.1.7. Variables initialised with `:=` sign have to be commented  
3.1.8. Within a function, any complex piece of code should have a comment explaining what is going on.  
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
	// Greatest Common Divisor
	var GCD Polynomial           
	// Factor and Divisor…
	var nominator, denominator natural.Natural 
	// Factor for…
	var multiplier rational.Rational           

	// Using Euclid`s algorythm
	for !((a.Older == 0 && rational.Compare(a.Coeff[0], rational.Zero()) == 0) ||
. . .
```
### 3.2. What should be avoided
3.2.1. If . . . else if . . . else
Try avoiding chains of if else statements if there is more than one condition.  
Use switch cases or returns instead.
