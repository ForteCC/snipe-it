You can achieve this by **forking** the open-source repository and setting up a workflow to **periodically sync updates** (especially security patches) from the original source. Here’s how you can do it:

### **1. Fork the Repository**
Fork the open-source repository to create your own version, which you can modify freely.

### **2. Set the Original Repository as an Upstream Remote**
To ensure you can pull future updates (security patches) from the original repository, configure it as an upstream remote.

Run these commands inside your cloned forked repository:
```sh
git remote add upstream https://github.com/original-owner/original-repo.git
git fetch upstream
```

### **3. Make Your Custom Changes in a Separate Branch**
Instead of modifying the `main` branch directly, create a new branch for your custom development:
```sh
git checkout -b my-custom-changes
```
This way, the `main` branch can always stay in sync with upstream changes.

### **4. Periodically Pull Security Updates**
Whenever you want to pull updates from the original repository, do:
```sh
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```
Then, merge the latest security patches into your custom branch:
```sh
git checkout my-custom-changes
git merge main
```

### **5. Automate Updates (Optional)**
You can automate the process using a **GitHub Action** that regularly fetches upstream changes and creates a PR in your repo.
But its better to do it manually to avoid system failer if there is a major change in source.
