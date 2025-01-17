# String Search and Manipulation Functions in Python

## Search Functions

1. **str.contains()**
   - Checks if a substring is present in each element of the Series.
   - Example:
      ```python
      df['column'].str.contains('substring')
      ```

2. **str.startswith()**
   - Checks if each element of the Series starts with a specified substring.
   - Example:
      ```python
      df['column'].str.startswith('substring')
      ```
      
3. **str.endswith()**
   - Checks if each element of the Series ends with a specified substring.
   - Example:
      ```python
      df['column'].str.endswith('substring')
      ```
      
4. **str.find()**
   - Returns the lowest index of the substring if it is found in the string. Returns -1 if not found.
   - Example:
      ```python
      string.find('substring')
      ```
        
5. **str.index()**
   - Similar to `str.find()`, but raises a `ValueError` if the substring is not found.
   - Example:
      ```python
      string.index('substring')
      ```

6. **str.count()**
   - Returns the number of non-overlapping occurrences of the substring in the string.
   - Example:
      ```python
      string.count('substring')
      ```

## Manipulation Functions

1. **str.lower()**
   - Converts all characters in the string to lowercase.
   - Example:
      ```python
      string.lower()
      ```

2. **str.upper()**
   - Converts all characters in the string to uppercase.
   - Example:
      ```python
      string.upper()
      ```

3. **str.capitalize()**
   - Capitalizes the first character of the string.
   - Example:
      ```python
      string.capitalize()
      ```

4. **str.title()**
   - Converts the first character of each word to uppercase.
   - Example:
      ```python
      string.title()
      ```
      
5. **str.strip()**
   - Removes leading and trailing whitespace from the string.
   - Example:
      ```python
      string.strip()
      ```
      
6. **str.lstrip()**
   - Removes leading whitespace from the string.
   - Example:
      ```python
      string.lstrip()
      ```

7. **str.rstrip()**
   - Removes trailing whitespace from the string.
   - Example:
      ```python
      string.rstrip()
      ```

8. **str.replace()**
   - Replaces occurrences of a substring with another substring.
   - Example:
      ```python
      string.replace('old', 'new')
      ```

9. **str.split()**
   - Splits the string into a list of substrings based on a delimiter.
   - Example:
      ```python
      string.split('delimiter')
      ```

10. **str.join()**
    - Joins a list of strings into a single string with a specified delimiter.
    - Example:
       ```python
       'delimiter'.join(list_of_strings)
       ```

11. **str.zfill()**
    - Pads the string on the left with zeros to fill a specified width.
    - Example:
       ```python
       string.zfill(width)
       ```

12. **str.pad()**
    - Pads the string with a specified character to fill a specified width.
    - Example:
       ```python
       string.pad(width, fillchar=' ')
       ```
      
13. **str.center()**
    - Centers the string within a specified width, padding with a specified character.
    - Example:
       ```python
       string.center(width, fillchar=' ')
       ```

14. **str.ljust()**
    - Left-justifies the string within a specified width, padding with a specified character.
    - Example:
       ```python
       string.ljust(width, fillchar=' ')
       ```

15. **str.rjust()**
    - Right-justifies the string within a specified width, padding with a specified character.
    - Example:
       ```python
       string.rjust(width, fillchar=' ')
       ```

## Regular Expressions

1. **re.search()**
   - Searches for a pattern in the string and returns a match object if found.
   - Example:
      ```python
      re.search(pattern, string)
      ```

2. **re.match()**
   - Checks if the beginning of the string matches the pattern.
   - Example:
      ```python
      re.match(pattern, string)
      ```

3. **re.findall()**
   - Returns a list of all non-overlapping matches of the pattern in the string.
   - Example:
      ```python
      re.findall(pattern, string)
      ```

4. **re.sub()**
   - Replaces occurrences of the pattern with a specified replacement string.
   - Example:
      ```python
      re.sub(pattern, replacement, string)
      ```

5. **re.split()**
   - Splits the string by occurrences of the pattern.
   - Example:
      ```python
      re.split(pattern, string)
      ```
