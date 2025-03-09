Here’s a cleaner and more structured version of your study notes:

---

# **Git: Cloning a Repo and Setting Up Upstream Remote**

## **1. Clone the Repository**

Navigate to your desired directory and clone the repository:

```bash
cd /path/to/your/directory
git clone https://github.com/username/repo.git
```

---

## **2. Navigate Into the Cloned Repo**

Move into the cloned repository:

```bash
cd repo
```

---

## **3. Set Up Upstream Remote**

### **Check Existing Remotes**

```bash
git remote -v
```

### **Add Upstream Remote**

```bash
git remote add upstream https://github.com/username/repo.git
```

### **Verify Upstream Remote**

```bash
git remote -v
```

### **Expected Output (Upon Success)**

```bash
origin    https://github.com/your-username/repository.git (fetch)
origin    https://github.com/your-username/repository.git (push)
upstream  https://github.com/original-user/original-repo.git (fetch)
upstream  https://github.com/original-user/original-repo.git (push)
```
