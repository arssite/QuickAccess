````
# 🔁 Migrate from pip to uv (Rust-Based Python Dependency Manager)

`uv` is a blazing-fast, Rust-based tool that replaces `pip`, `virtualenv`, and `pip-tools`. It's ideal for modern Python workflows. This guide walks you through completely switching from `pip` to `uv`.

---

## 🚀 Why use `uv` instead of `pip`?

| Feature               | pip (Python-based)      | uv (Rust-based)           |
|-----------------------|-------------------------|----------------------------|
| Speed                 | 🐢 Slower                | ⚡ 2x–10x faster            |
| Dependency resolution | ❌ Sequential            | ✅ Parallel + fast          |
| Language              | Python                  | Rust                       |
| Virtualenv support    | Requires `venv` or `virtualenv` | Built-in              |
| Lock file support     | ❌ (use pip-tools)       | ✅ Native support           |
| Pyproject.toml usage  | ❌ Manual setup          | ✅ First-class citizen      |

---

## ⚙️ Step 1: Install `uv`

Install globally via `pipx` (recommended) or `pip`:

```bash
# Recommended
pip install pipx
pipx install uv

# Or fallback
pip install uv
````

Verify:

```bash
uv --version
```

---

## 📁 Step 2: Setup Your Environment

### ✅ Option A: Fresh project (best practice)

```bash
uv init
```

This creates a `pyproject.toml` and sets up the environment. Then:

```bash
uv install flask requests
```

### ✅ Option B: Existing project with `requirements.txt`

```bash
uv venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

uv install -r requirements.txt
```

---

## 🔁 Step 3: Replace pip Commands with uv

| Task                      | pip                      | uv                        |
| ------------------------- | ------------------------ | ------------------------- |
| Create virtualenv         | `python -m venv venv`    | `uv venv venv`            |
| Install a package         | `pip install flask`      | `uv install flask`        |
| Install from file         | `pip install -r req.txt` | `uv install -r req.txt`   |
| Freeze environment        | `pip freeze > req.txt`   | `uv pip freeze > req.txt` |
| Sync exact deps from lock | (pip-tools required)     | `uv sync`                 |
| Init project with config  | Manual                   | `uv init`                 |

---

## 🔄 Step 4: Convert to pyproject.toml

Want to move away from `requirements.txt`?

```bash
uv convert-requirements requirements.txt
```

Then, just use:

```bash
uv install
```

And `uv` handles everything.

---

## 🧹 Step 5: Remove `pip` Usage

To fully commit to `uv`:

* Use `pyproject.toml` instead of `requirements.txt`
* Use `uv install`, `uv sync`, `uv pip freeze`
* Avoid `pip install`, `pip freeze`, `venv`, `pip-tools`

---

## 📚 Resources

* 📘 [uv GitHub Repo](https://github.com/astral-sh/uv)
* 📖 [uv Documentation](https://docs.astral.sh/uv/)
* 📑 [PEP 621: pyproject.toml metadata](https://peps.python.org/pep-0621/)

---

Happy hacking with ⚡ `uv`!


---

## ✅ Full Migration Guide to `uv` (No `pip` Involved)

---

### 🔧 1. **Create a Virtual Environment with `uv`**

```bash
uv venv ars
```

This replaces `python -m venv ars`.

Then activate it:

* **Windows (CMD):**

  ```bash
  ars\Scripts\activate
  ```

* **Linux/macOS:**

  ```bash
  source ars/bin/activate
  ```

---

### 📦 2. **Install Packages (No `pip`)**

Instead of:

```bash
pip install flask
```

Use:

```bash
uv install flask
```

You can also install from a file:

```bash
uv install -r requirements.txt
```

---

### 📜 3. **Track Dependencies**

Instead of `pip freeze`, use:

```bash
uv pip freeze > requirements.txt
```

Or switch to the `pyproject.toml` format (recommended for serious projects):

```bash
uv init
```

Then install like this:

```bash
uv install
```

---

### 📁 4. **Remove `pip` Usage**

You can uninstall `pip` if you're hardcore, but usually it's safer to just **ignore it**. Just avoid:

* `pip install`
* `pip freeze`
* `virtualenv`
* `python -m venv`

---

### 🔄 Bonus: Convert `requirements.txt` to `pyproject.toml`

If you're migrating:

```bash
uv convert-requirements requirements.txt
```

This will generate a `pyproject.toml`, and you can continue using:

```bash
uv install
uv sync
```

---

### 🔁 Common `uv` Commands

| Task              | `pip` Equivalent         | `uv` Command            |
| ----------------- | ------------------------ | ----------------------- |
| Create venv       | `python -m venv venv`    | `uv venv venv`          |
| Install packages  | `pip install ...`        | `uv install ...`        |
| Install from file | `pip install -r req.txt` | `uv install -r req.txt` |
| Freeze versions   | `pip freeze`             | `uv pip freeze`         |
| Sync env          | (via pip-tools)          | `uv sync`               |
| Init project      | (manual setup)           | `uv init`               |




