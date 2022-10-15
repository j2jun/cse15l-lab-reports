# Week 3 Lab Report

## 1. Part 1
**Search Engine Code**

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
1. ![2](https://user-images.githubusercontent.com/54129361/195956481-6b1ddd17-7bd1-43a6-82ed-9121bca3af87.png)

        - This shows when you want to add a new string of list. This erases all the previous strings that were stored. Anything after the "=" is stored as a string. 

2. ![5](https://user-images.githubusercontent.com/54129361/195956578-07412c07-3cf5-474f-bc1c-a8fe2c5ade58.png)

        - This adds a string to the list of strings. 

3. ![6](https://user-images.githubusercontent.com/54129361/195956534-8aac2eff-a51e-422a-90bb-f13593f63d29.png)

        - This searches for any strings that have a substring, which was written after "search?s="

## 2. Part Two
**Bugs & Tests**

    1.
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
    
    
    2.
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
