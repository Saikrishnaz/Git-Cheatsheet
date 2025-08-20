# Git Submodules

## 1. What is a Submodule?
- A **submodule** is a Git repository inside another Git repository.  
- Useful when your project depends on another repo (e.g., a library or separate module).  
- Example: You have a **main repo** (`mainrepo`), and inside it you want to include another repo (`LoginUsers`) under `SAI/`.  

---

## 2. Adding a Submodule

1. Navigate to your main repo:  
   ```bash
   cd mainrepo
   ```

2. Add the submodule inside your desired folder (`SAI/`):  
   ```bash
   git submodule add https://github.com/username/LoginUsers.git SAI/LoginUsers
   ```

   - This creates the folder `SAI/LoginUsers` and links it to the external repo.  

3. Commit the submodule reference:  
   ```bash
   git commit -m "Added LoginUsers as a submodule"
   ```

---

## 3. Cloning a Repo with Submodules

When someone clones your main repo, they need to initialize and fetch submodules:  

```bash
git clone https://github.com/username/mainrepo.git
cd mainrepo
git submodule init
git submodule update
```

Or clone everything in one step:  

```bash
git clone --recurse-submodules https://github.com/username/mainrepo.git
```

---

## 4. Updating Submodules

If changes are made in the `LoginUsers` repo:  

```bash
cd SAI/LoginUsers
git pull origin main   # fetch latest changes
```

Then go back to main repo and commit the updated submodule reference:  

```bash
cd ../..
git add SAI/LoginUsers
git commit -m "Updated LoginUsers submodule"
```

---

## 5. Removing a Submodule

```bash
git submodule deinit -f SAI/LoginUsers
git rm -f SAI/LoginUsers
rm -rf .git/modules/SAI/LoginUsers
```

---

## 6. Best Practices for Submodules
- Use submodules only when the external repo is managed separately.  
- If you frequently modify both repos, consider **monorepo structure** instead.  
- Always update submodules after cloning.  
- Commit submodule references immediately after updating.  

---
