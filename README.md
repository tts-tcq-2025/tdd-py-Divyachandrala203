# TDD Driven StringCalculator

Build a StringCalculator functionality that can take up to two numbers, separated by commas, and will return their sum. 
for example “” or “1” or “1,2” as inputs.

> DO NOT jump into implementation! Read the example and the starting task below.

- For an empty string it will return 0
- Allow the Add method to handle an unknown amount of numbers
- Allow the Add method to handle new lines between numbers (instead of commas).
  - the following input is ok: “1\n2,3” (will equal 6)
  - the following input is NOT ok: “1,\n” (not need to prove it - just clarifying)
- Support different delimiters : to change a delimiter, the beginning of the string will contain a separate line that looks like this: “//[delimiter]\n[numbers…]” for example “//;\n1;2” should return three where the default delimiter is ‘;’ .
the first line is optional. all existing scenarios should still be supported
- Calling Method with a negative number will throw an exception “negatives not allowed” - and the negative that was passed. if there are multiple negatives, show all of them in the exception message.
- Numbers bigger than 1000 should be ignored, so adding 2 + 1001 = 2
- Delimiters can be of any length with the following format: “//[delimiter]\n” for example: “//[***]\n1***2***3” should return 6

## Tasks



Establish quality parameters:

- Ensure  maximum complexity (CCN) per function == 3

- Ensure 100% line and branch coverage at every step

  

Start Test-driven approach

1. Write the smallest possible failing test: give input `"" assert output to be 0 ` .
2. Write the minimum amount of code that'll make it pass.
3. Refactor any assumptions, continue to pass this test. Do not add any code without a corresponding test.

test specification:
Basic Functionality
1. Empty string returns 0 -"" - 0
2. Single number returns the number itself - "5" - 5
3. Two numbers separated by comma are summed - "1,2" - 3
4. Multiple numbers separated by comma are summed - "1,2,3" - 6
Handling Newlines
1. Newline as delimite - "1\n2,3" - 6
2. Invalid delimiter format throws exception -"1,\n" - Exception or error handling
Custom Delimiters
1. Custom single-character delimiter - "//;\n1;2" - 3
2. Custom multi-character delimiter -"//[***]\n1***2***3" - 6
3. Multiple custom delimiters -"//[*][%]\n1*2%3" - 6
Negative Numbers
1. Negative numbers throw exception - "1,-2" - Exception with message "Negatives not allowed: -2"
2. Multiple negative numbers listed in exception - "1,-2,-3" - Exception with message "Negatives not allowed: -2, -3"
Edge Cases
1. Input with spaces - " 1 , 2 " (input)- 3(expected output)
2. Input with trailing delimiter - "1,2," - Exception or error handling

gherkin
Test Case ID	Test Name	Input	Expected Output / Behavior
TC01	Empty string returns zero	""	0
TC02	Single number returns itself	"5"	5
TC03	Two numbers separated by comma	"1,2"	3
TC04	Multiple comma-separated numbers	"1,2,3"	6
TC05	Newline as delimiter	"1\n2,3"	6
TC06	Invalid delimiter format	"1,\n"	Exception or error
TC07	Custom single-character delimiter	"//;\n1;2"	3
TC08	Custom multi-character delimiter	"//[***]\n1***2***3"	6
TC09	Multiple custom delimiters	"//[*][%]\n1*2%3"	6
TC10	Negative number throws exception	"1,-2"	Exception: "Negatives not allowed: -2"
TC11	Multiple negatives in exception	"1,-2,-3"	Exception: "Negatives not allowed: -2, -3"
TC12	Numbers >1000 are ignored	"2,1001"	2
TC13	1000 is included	"2,1000"	1002
TC14	Input with spaces	" 1 , 2 "	3
TC15	Trailing delimiter throws exception	"1,2,"	Exception or error

    
