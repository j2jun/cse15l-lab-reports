# Week 7: Lab Report 4 - VIM

## Part 1 - Changing the name of the *start* parameter and its uses to *base*
---

```
/start<enter>cebase<esc>n.n.:w<enter>
```

* ```/start<enter>``` - the cursor jumps to the front of “start”
  
  ![image](https://user-images.githubusercontent.com/54129361/201615831-ed4f36a7-7c8b-4327-9e82-8a6627d5351e.png)

* ```ce``` - The cursor will change to insert mode and deletes the word “start”
  
  ![image](https://user-images.githubusercontent.com/54129361/201615926-5c1b1994-940a-49ab-9969-eba5d05ff450.png)

* ```base<esc>``` – Type in “base” and exit the insert mode
  
  ![image](https://user-images.githubusercontent.com/54129361/201616181-e32ce73d-7ac7-46c9-bc61-07cbad7955e5.png)

* ```n``` – searches the last search command (/start) from the current cursor’s position
  
  ![image](https://user-images.githubusercontent.com/54129361/201616271-b35b003f-12a4-4b06-b023-cff3b5138f7b.png)

* ```.``` - Repeats the last insert command, which was to replace “start” to “base”
  
  ![image](https://user-images.githubusercontent.com/54129361/201616418-409d1204-e857-4d56-b476-bc5854c7fd70.png)

* ```n.``` – like above, searches the word, “start,” and replaces that word to “base”
  
  ![image](https://user-images.githubusercontent.com/54129361/201616510-0ede325b-dad9-4f3b-8f39-1cd6d75449c2.png)

* ```:w<enter>``` - saves the changes
  
  ![image](https://user-images.githubusercontent.com/54129361/201616598-5919064f-faa0-4e4f-bb99-a18128943d49.png)

  
## Part 2 - Questions
---
  
* **Report how long it took you to make the edit in seconds in both styles, and any difficulties or details that came up in doing so.**
  
  The first way, which is editing from local computer and scp to remote server, takes about 7 minutes 30 seconds.
  The second way, which is editing from the remote server using VIM, takes about 7 minutes.
  
* **Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?**
  
  If I had to work on a program that I was running remotely, I would prefer the second way because constantly changing from scp from the local computer to remote server is very annoying and time consuming.
  
* **What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)**
  
  I believe the memory and the organization of files are the deciding factors into my decision. Sometimes, it is much easier to run locally and use scp to copy all the changes that are made. However, if it requires less change; it can be much easier to directly edit from the remote server.
