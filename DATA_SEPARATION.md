# Data Separation - How It Works

## What Changed

Your portfolio now loads all data from the **`data.json`** file instead of having it hardcoded in `index.html`.

## How It Works

1. **Vue.js loads on page open**
   - The HTML file initializes with an empty `profile` object

2. **Data fetches automatically**
   - When the page loads, the `mounted()` function runs
   - It fetches data from `./data.json`
   - The profile object gets populated with the data

3. **Template renders dynamically**
   - Vue.js automatically updates the view when data loads
   - Everything displays normally after ~100ms

## File Structure

```
index.html              ← Vue app with fetch logic
    ↓ (fetches at startup)
data.json               ← All your portfolio data
```

## Editing Your Portfolio

**To change content, edit `data.json` only!**

Example:
```json
{
  "profile": {
    "fullName": "Your Name",         ← Change this
    "title": "Your Title",           ← Change this
    "social": {
      "github": "your-url"           ← Change this
    }
    // ... all other content
  }
}
```

Then **save the file** and **refresh the browser** - changes appear instantly!

## Benefits

✅ **Cleaner HTML** - No huge data object cluttering the code  
✅ **Easier updates** - Edit one JSON file, not HTML  
✅ **Better organization** - Content separated from logic  
✅ **GitHub Pages ready** - Still works perfectly  
✅ **Future scalability** - Easy to add database later  

## How to Test Locally

1. **Open a terminal** in the portfolio folder
2. **Start a simple server:**
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Or Python 2
   python -m SimpleHTTPServer 8000
   
   # Or Node.js (with npx)
   npx http-server
   ```

3. **Visit:** `http://localhost:8000`
4. **Open browser DevTools** (F12) to check for errors
5. **Look at Console** - You should see your data loaded

## Fetch Path Explanation

The code uses `./data.json` which means:
- `./` = current directory
- `data.json` = the file in that directory
- Works locally and on GitHub Pages

## Error Handling

If `data.json` can't be found:
- Check browser Console (F12)
- You'll see: `Error loading data.json: [error details]`
- Make sure `data.json` is in the same folder as `index.html`

## Mobile Testing

The data loading works the same way on mobile - completely transparent to the user.

## Deployment (GitHub Pages)

**No changes needed!** Just push both files:
```bash
git add .
git commit -m "Separate data into data.json"
git push
```

Everything works the same on GitHub Pages.

---

**You now have cleaner, more maintainable code!** 🎉

Just edit `data.json` whenever you want to update your portfolio.
