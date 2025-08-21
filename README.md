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
Feature: String Calculator

  Scenario: Empty string returns zero
    Given the input is an empty string
    When I call the add method
    Then the result should be 0

  Scenario: Single number returns the number itself
    Given the input is "5"
    When I call the add method
    Then the result should be 5

  Scenario: Two numbers separated by comma are summed
    Given the input is "1,2"
    When I call the add method
    Then the result should be 3

  Scenario: Multiple numbers separated by comma are summed
    Given the input is "1,2,3"
    When I call the add method
    Then the result should be 6

  Scenario: Newline as delimiter
    Given the input is "1\n2,3"
    When I call the add method
    Then the result should be 6

  Scenario: Custom single-character delimiter
    Given the input is "//;\n1;2"
    When I call the add method
    Then the result should be 3

  Scenario: Custom multi-character delimiter
    Given the input is "//[***]\n1***2***3"
    When I call the add method
    Then the result should be 6

  Scenario: Multiple custom delimiters
    Given the input is "//[*][%]\n1*2%3"
    When I call the add method
    Then the result should be 6

  Scenario: Negative numbers throw exception
    Given the input is "1,-2"
    When I call the add method
    Then an exception should be thrown with message "Negatives not allowed: -2"

  Scenario: Multiple negative numbers listed in exception
    Given the input is "1,-2,-3"
    When I call the add method
    Then an exception should be thrown with message "Negatives not allowed: -2, -3"

  Scenario: Numbers greater than 1000 are ignored
    Given the input is "2,1001"
    When I call the add method
    Then the result should be 2

  Scenario: 1000 is included
    Given the input is "2,1000"
    When I call the add method
    Then the result should be 1002

  Scenario: Input with spaces
    Given the input is " 1 , 2 "
    When I call the add method
    Then the result should be 3

  Scenario: Input with trailing delimiter
    Given the input is "1,2,"
    When I call the add method
    Then an exception should be thrown
