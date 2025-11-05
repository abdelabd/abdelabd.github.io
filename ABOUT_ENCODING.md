# About.md Encoding Workflow

## The Problem
VS Code on Windows saves `about.md` as UTF-16, which breaks markdown link rendering on the website.

## The Solution
Edit a separate UTF-16 file and convert it to UTF-8 before committing.

## Workflow

### 1. Edit the content
**For example, edit `content/markdown/about.md`

### 2. Convert to UTF-8
On bottom right, where it says `UTF-X`, click on that, then click on `Save with encoding`, then click on `utf8bom`.

**Option A - Python:**
```bash
python convert_about.py
```

**Option B - Batch file (Windows):**
```bash
convert_about.bat
```

### 3. Commit and push
```bash
git add content/markdown/about.md .gitignore
git commit -m "Update about content"
git push origin main
```

## Files
- `content/markdown/about_utf16.md` - Your working file (UTF-16, ignored by git)
- `content/markdown/about.md` - Published file (UTF-8, committed to git)
- `convert_about.py` - Conversion script
- `convert_about.bat` - Windows batch file for quick conversion

## Note
The `about_utf16.md` file is in `.gitignore` so it won't be committed. Only the UTF-8 version (`about.md`) gets pushed to GitHub.
