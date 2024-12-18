# Write-Up: Easy - Micro-CMS v1 🛠️  
**Platform**: Hacker101 CTF  
**Category**: Web  
**Difficulty**: Easy  
**Tools Used**: Browser Developer Tools, URL Manipulation  

---

## Challenge Description  
The challenge **"Easy - Micro-CMS v1"** involves a small content management system (CMS). The hint provided was:  
> "Try creating a new page and think about how pages are indexed."  

The goal is to find a flag by identifying weaknesses in how the CMS handles page IDs.

---

## Step-by-Step Solution

### 1. **Create a New Page**  
- On the CMS interface, I found an option to **create a new page**.  
- After creating the page, I noticed the **URL** contained an **ID parameter** in the query string, such as:  
  ```
  http://example.com/page/edit/20
  ```
  Here, `20` is the ID of the page I created.

---

### 2. **Inspect the URL Structure**  
- Based on the hint ("how pages are indexed"), I hypothesized that the page IDs were **sequential**.  
- I tried **manipulating the ID parameter** in the URL by changing `20` to `6`:
  ```
  http://example.com/page/edit/6
  ```

---

### 3. **Accessing Unauthorized Page**  
- Upon changing the ID to `6`, I was able to access a **different page** that I had not created.  
- The new page revealed the **flag** because the application failed to enforce proper access controls.

---

## Root Cause: **Insecure Direct Object Reference (IDOR)**  
The CMS suffered from an **IDOR vulnerability**:
- The application relied on predictable page IDs (sequential numbers) without verifying if the user had permissions to access specific pages.
- By tampering with the `id` parameter, I accessed content belonging to other users or administrators.

---

## Flag
```
flag{example_flag_found}
```

---

## Key Takeaways 📝

1. **Insecure Direct Object Reference (IDOR)**:
   - Always test for predictable IDs in URLs or parameters. IDOR is a common web vulnerability caused by missing access controls.

2. **Parameter Tampering**:
   - Manipulating values in the URL or form fields can expose hidden or unauthorized content.

3. **Sequential Indexing**:
   - Applications that use sequential IDs (e.g., `1, 2, 3...`) are often vulnerable to IDOR attacks. Testing for other IDs can help uncover unintended data.

---

## Lessons Learned
- **Check How Resources Are Indexed**: Always test how pages, users, or resources are referenced in URLs.
- **Access Control Matters**: Proper access controls must be implemented to ensure users can only access resources they own or have permission for.
- **Simple Manipulation Can Yield Results**: Sometimes, a small change in a URL parameter can expose significant vulnerabilities.

---

## Final Thoughts  
This challenge highlights the importance of testing for **IDOR** vulnerabilities and parameter tampering, both of which are common in bug bounty programs and real-world web applications.