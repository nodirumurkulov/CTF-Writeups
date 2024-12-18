# Write-Up: Trivial - A Little Something to Get You Started 🎯  
**Platform**: Hacker101 CTF  
**Category**: Web  
**Difficulty**: Trivial  
**Tools Used**: Browser Developer Tools  

---

## Challenge Description  
The challenge **"Trivial - A little something to get you started"** hints at looking into the **source code** of the webpage to find the flag. The objective is to uncover a hidden flag without using any advanced tools.

---

## Step-by-Step Solution

1. **Open the Challenge Page**:  
   - Access the provided URL in your browser.

2. **View the Source Code**:  
   - Right-click on the page and select **"View Page Source"** (or press `Ctrl+U` / `Cmd+Option+U`).

3. **Search for the Flag**:  
   - Use the browser's search feature (`Ctrl+F`) to look for common keywords like `flag`, `ctf`, or `{`.

4. **Flag Found**:  
   - In the source code, you’ll find a line containing the flag, which might look something like:
     ```html
     <!-- flag{this_is_your_flag_here} -->
     ```

---

## Key Takeaways 📝
- **Source Code Analysis**: Always check the page source for hints, comments, or hidden flags in basic challenges.
- **Browser Tools**: You don’t need advanced tools for initial web CTF tasks; a browser is often enough.
- **CTF Mindset**: Start simple. If the challenge hints at the source, don’t overthink it.

---

## Flag
```
flag{example_flag_found}
```

---

## Lessons Learned
This challenge teaches you the importance of:
1. **Looking for Low-Hanging Fruits**: In CTFs, the simplest vulnerabilities or clues often yield the solution.
2. **Using Developer Tools**: Browser tools like **View Source** and **Inspect Element** are fundamental for web security testing.
3. **Attention to Hints**: Always follow the hint provided in the challenge; it’s there for a reason.

---

### Final Thoughts
This is a great starting point for beginners in web security CTFs. It emphasizes simple steps that are often overlooked but can lead to quick wins.