# Overview

This repository is a part of the Java language training plan. Please read the following guidelines before start.

# Getting Start

## Basic Principals

Each repository contains a gradle java project with a number of unit tests. The initial state of all unit tests are *FAILED*. So the aim is to correct the failed test. Please follow the following steps to get the best experience:

* Read the test code and try to understand what it says.
* Trying to fix the test **WITHOUT RUNNING**. This is very important. Because once you run the test, you may find the failure message of the test telling you the expected result. That means you may lose the chance to figure it out by yourself. Note that you should **ONLY** be able to modify code within the **TODO AREA**. The code outside the **TODO AREA** is **NOT** changable.
* Run the test to examine if the fix is correct.
* Answer the following 4 questions after the test is passed.

The 4 questions are:

1. What is the knowledge point of the test? Where is the offical document to the knowledge point?
1. Why the test failed at first?
1. Why you corrected the test that way?
1. Do you have further questions on this knowledge point?

None.

## Example

Let's take a look at an example:

```java
@Test
void should_pass_by_value() {
  int value = 5;

  tryingToUpdateValue(value);

  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 0;
  // --end-->

  assertEquals(expected, value);
}
```

First, read the test. From the title and code we can know that the test what to examine the behavior when passing an argument. We are not sure what `tryingToUpdateValue` does, so we can jump into its implementation:

```java
private static void tryingToUpdateValue(int value) {
  value += 2;
}
```

Now we have got the full context of the test. The argument is passed by value so the integer will be copied when passing into `tryingToUpdateValue`. Thus the value from the caller site will not change.

Notice that the todo area is in the test method. So we can modify codes within the todo area to pass the test:

```java
  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 5;
  // --end-->
```

Please note that not all todo areas are located in test method. And some todo area may have further restrictions, for example:

```java
  // TODO: You should not write concrete number here. Please find a property or constant instead.
  // <!--start
  final int maximumSymbol = 0;
  final int minimumSymbol = 0;
  // --end-->
```

The hint indicates that we should not write concrete number here. So I should not write `3` or `0xffffffff`, but write symbol (e.g. `Integer.MAX_VALUE`).

## Running Test

You could run unit tests with the help of IntelliJ. But it is also possible to run unit test via command line: `./gradlew build`.

If you just want to build your code without running test. Please use `./gradlew build -x test
`

- ANSWERS

1. What is the knowledge point of the test? Where is the official document to the knowledge point?

    * should_be_immutable - To know how to get the modified string that are have a replaced string.
    * all_modification_method_will_create_new_string - To know what is the use of trim() method.
    * will_create_new_string_when_concat - To know how to concat the given strings in a different variables.
    * should_taken_string_apart - To know what is the use of replace() method.
    * should_taken_string_apart_continued - To know what is the use of replace() method.
    * should_break_string_into_words - To know how to split the strings, and put it in an array string.
    * should_break_string_into_words_customized - To know how to split the strings depending on what character is placed between the message string.
    * should_create_ascii_art - To know how to get the ascii art actual values.
    * should_calculate_checksum_of_a_string - To know how to calculate the sum of each text.
    * should_convert_unicode_escape - To know how to use the unicode escape values.
    * should_reverse_a_string - To know how to reverse a given string.
    * should_compare_string_with_different_cases - To know how to get the result depending if the actual values is upperCase or lowerCase.
    * should_format_string - To know how to use the String.format() method.

1. Why the test failed at first?

    * should_be_immutable - The Optional value is still empty, and it should be the modified value.
    * all_modification_method_will_create_new_string - The Optional value is still empty, and it should be the modified value.
    * will_create_new_string_when_concat - The Optional value is still empty, and it should be the concatenated value.
    * should_taken_string_apart - No expected value that should be the expected string, depending on what is being replaced on actual string.
    * should_taken_string_apart_continued - No expected value that should be the expected string, depending on what is being replaced on actual string.
    * should_break_string_into_words - The array string is null.
    * should_break_string_into_words_customized - The array string is null.
    * should_create_ascii_art - The expected value is null, and should be equal to what ascii art is created.
    * should_calculate_checksum_of_a_string - There are no calculation of each character in a given string.
    * should_convert_unicode_escape - There are no unicode escape values in the expected string.
    * should_reverse_a_string - The given string is not yet reversed.
    * should_compare_string_with_different_cases - The expected values does not have any Optional values, depending if the upperCase ignores the lowerCase value, or upperCase is not equal to lowerCase value.
    * should_format_string - There are no expected values, depending on what is the value from the formatted string.

1. Why you corrected the test that way?

    * should_be_immutable - Modified string is equal to what is the specified string that is modified.
    * all_modification_method_will_create_new_string - Modified string should be the original string, and the leading and trailing spaces are being eliminated.
    * will_create_new_string_when_concat - Modified string is equal to what strings are being concatenated.
    * should_taken_string_apart - Modified string is equal to what string is replaced on original string.
    * should_taken_string_apart_continued - Modified string is equal to what string is replaced on original string.
    * should_break_string_into_words - The expected result is depending on what is the character that is between the message, which is " ", and put it in the array string.
    * should_break_string_into_words_customized - The expected result is depending on what is the character that is between the message, which is "/",and put it in the array string.
    * should_create_ascii_art - Used for loop depending on what values are given in height and width.
    * should_calculate_checksum_of_a_string - Used for loop and charAt() method to get the value of each string, to add the values consecutively.
    * should_convert_unicode_escape - The unicode escape strings are given already. Therefore, concatenating the unicode escape and place it in the expected value will pass the test.
    * should_reverse_a_string - Used StringBuilder, and reverse() function to reverse the character that is being appended to the StringBuilder.
    * should_compare_string_with_different_cases - First actual value does not ignore the cases. Therefore, it should return false since upperCase value is not equal to lowerCase value. Second actual value ignores the cases. Therefore, it should return as true since the values are equal, no matter if it is upperCase or lowerCase string.
    * should_format_string - The formatted string is already given.

1. Do you have further questions on this knowledge point?

    * None.