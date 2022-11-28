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

1. This shows when you want to add a new string of list. This erases all the previous strings that were stored. Anything after the "=" is stored as a string. This has a several method calls for getPath(), contains(), getQuery(), split(), and format(). contains() checks you if you contain a certain phrase. getQuery() and split() pulls out the substring from the URL that we want to add. equals() compares to check if the URL is formatted correctly. add() stores a new string to the list. format() prints out the string with a certain format. Basically, getPath() will pull the path and checks if it has "add" by using contains(). getQuery() will pull out the query and split will split "?" from the substring after "?." If the query contains "anewstringtoadd," new list will be created. format() will print out certain format that is coded.

![5](https://user-images.githubusercontent.com/54129361/195956578-07412c07-3cf5-474f-bc1c-a8fe2c5ade58.png)

2. This adds a string to the list of strings. This has a several method calls for getPath(), contains(), getQuery(), split(), add(), and format(). contains() checks you if you contain a certain phrase. getQuery() and split() pulls out the substring from the URL that we want to add. equals() compares to check if the URL is formatted correctly. add() stores a new string to the list. format() prints out the string with a certain format. This step is similar to the above, but this will add new string to the list, instead of creating a new list. format() will print out all the string in the list.

![6](https://user-images.githubusercontent.com/54129361/195956534-8aac2eff-a51e-422a-90bb-f13593f63d29.png)

3. This searches for any strings that have a substring, which was written after "search?s=". This has a several method calls for getPath(), contains(), getQuery(), split(), and format(). contains() checks you if you contain a certain phrase. getQuery() and split() pulls out the substring from the URL that we want to add. equals() compares to check if the URL is formatted correctly. add() stores a new string to the list. format() prints out the string with a certain format. Using contains(), this will print out all the string that contains substring that is after the equal (=) sign in format().

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
   In order to fix this bug, you need to create a temporary integer. You store the temporary integer with the array list at the current index. After storing, you set the index to "arr.length - i - 1." Now, you need to set the array list at the "arr.length - i - 1" to the temporary integer. Basically, you swap the order by using the temporary integer.

   - The connection between the symptom & the bug:
      After flipping half of the array list, ReverseInPlace shows bug that the other half reverses itself.
 
    
   2. **filter() from List Methods**
   - Failure-inducing input:
   ```
    @Test
    public void merge() {
        List<String> list1 = new ArrayList<String>();
        List<String> list2 = new ArrayList<String>();
        List<String> expected = List.of("apple", "banana", "dog", "monkey", "orange");

        list1.add("banana");
        list1.add("apple");
        list1.add("orange");
        list2.add("monkey");
        list1.add("monkey");
        list2.add("banana");
        list2.add("dog");
        assertEquals(expected, ListExamples.merge(list1, list2));
    }
   ```

   - Symptom:
  ![image](https://user-images.githubusercontent.com/54129361/198423706-479d0e46-03d5-4a5a-959a-ed62d5d23459.png)

   - Bug:
   ![1](https://user-images.githubusercontent.com/54129361/198423745-3ccd7682-280d-46b1-b467-3f87d2301259.png)

   
   In order to fix this bug, you need change the bottom section of code. If you look at the last while loop, you can see the index1 increments, not index2. You need to change to index 2, so it won't be an infinite loop. Aftr changing to index 2, the code will work.
   
   - The connection between the symptom & the bug:
      The connection between the symptom & the bug is that the loop will never end since only index1 is incrementing. 
   
