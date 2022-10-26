# Week 3 Lab Report by *Joseph Jun*

## 1. Part One
**Search Engine Code**
The following is my code for a search engine that tracks a list of strings, adds a new string to the list, and returns a list of all strings that have a given substring.

   ```
    List<String> strList = new ArrayList<String>();
    
    public String handleRequest(URI url) {
        if (url.getPath().contains("/")) {
            if (url.getPath().contains("add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].contains("s")) {
                    if (parameters[1].contains("anewstringtoadd")) {
                        strList = new ArrayList<String>();
                        return String.format("%s", strList);
                    } else {
                        strList.add(parameters[1]);
                        return String.format("%s", strList);
                    }
                } else {
                    return "404 Not Found!";
                }
            } else if (url.getPath().contains("search")) {
                String[] parameters = url.getQuery().split("=");
                List<String> found = new ArrayList<String>();

                if (parameters[0].contains("s")) {

                    for (String str : strList) {
                        if (str.contains(parameters[1])) {
                            found.add(str);
                        }
                    }
                }
                return String.format("%s", found);

            } else {
                return String.format("%s", strList);
            }
        }
        return "404 Not Found!";
    }
   ```
    
**Screenshot**
![2](https://user-images.githubusercontent.com/54129361/195956481-6b1ddd17-7bd1-43a6-82ed-9121bca3af87.png)

1. This shows when you want to add a new string of list. This erases all the previous strings that were stored. Anything after the "=" is stored as a string. This has a several method calls for getPath(), contains(), getQuery(), split(), and format(). contains() checks you if you contain a certain phrase. getQuery() and split() pulls out the substring from the URL that we want to add. equals() compares to check if the URL is formatted correctly. add() stores a new string to the list. format() prints out the string with a certain format.

![5](https://user-images.githubusercontent.com/54129361/195956578-07412c07-3cf5-474f-bc1c-a8fe2c5ade58.png)

2. This adds a string to the list of strings. This has a several method calls for getPath(), contains(), getQuery(), split(), and format(). contains() checks you if you contain a certain phrase. getQuery() and split() pulls out the substring from the URL that we want to add. equals() compares to check if the URL is formatted correctly. add() stores a new string to the list. format() prints out the string with a certain format.

![6](https://user-images.githubusercontent.com/54129361/195956534-8aac2eff-a51e-422a-90bb-f13593f63d29.png)

3. This searches for any strings that have a substring, which was written after "search?s=". This has a several method calls for getPath(), contains(), getQuery(), split(), and format(). contains() checks you if you contain a certain phrase. getQuery() and split() pulls out the substring from the URL that we want to add. equals() compares to check if the URL is formatted correctly. add() stores a new string to the list. format() prints out the string with a certain format.

---

## 2. Part Two
**Bugs & Tests**

   1. **testReverseInPlace() from Array Methods**
   - Failure-inducing input:
  ```
    @Test
    public void testReverseInPlace() {
        int[] testArray = { 1, 2, 3, 4, 5 };
        int[] expected = { 5, 4, 3, 2, 1 };
        ArrayExamples.reverseInPlace(testArray);
        assertArrayEquals(expected, testArray);
    }
  ```
   - Symptom:
   ![Test1 Fail Output](https://user-images.githubusercontent.com/54129361/195962943-a9bd5839-3fe1-47ee-9aaf-94529a915fbe.png)
   
   - Bug:
   ```
    // Changes the input array to be in reversed order
    static void reverseInPlace(int[] arr) {
        for(int i = 0; i < arr.length; i += 1) {
            arr[i] = arr[arr.length - i - 1];
        }
    }
   ```

   - The connection between the symptom & the bug:
      After flipping half of the array list, ReverseInPlace shows bug that the other half reverses itself.
      
   - Fixed Code:
   ![image](https://user-images.githubusercontent.com/54129361/198150969-8997c4c5-9a69-4baa-91d9-6499dfb121b9.png)
 
    
   2. **filter() from List Methods**
   - Failure-inducing input:
   ```
    @Test
    public void filter() {
        List<String> test = List.of("India", "China", "Bhutan");
        List<String> expected = List.of("India", "China", "Bhutan");
        StringChecker sc = new Checker();
        assertEquals(expected, ListExamples.filter(test, sc));
    }
   ```

   - Symptom:
  ![Test 2 Fail Output](https://user-images.githubusercontent.com/54129361/195963316-e6b04c64-d624-432c-b955-55a8d3ab044a.png)

   - Bug:
   ```
    // Returns a new list that has all the elements of the input list for which
    // the StringChecker returns true, and not the elements that return false, in
    // the same order they appeared in the input list;
    static List<String> filter(List<String> list, StringChecker sc) {
        List<String> result = new ArrayList<>();
        for(String s: list) {
            if(sc.checkString(s)) {
                result.add(0, s);
            }
        }
        return result;
    }
   ```

   - The connection between the symptom & the bug:
      Strings that needed to be added to the list were replacing the first index only.
      
   - Fixed Code:
   
