# exposepy

**exposepy** is a minimalist Python library that makes your public API explicit, refactor-proof, and automatic.

No more boilerplate. No more forgotten `__all__`. Just declare what you want public.

---

## 📦 Installation

```bash
pip install exposepy
```

---

## 🧠 Why use exposepy?

- ✅ Zero-boilerplate API exposure with `@expose`
- ✅ Automatic `__all__` population
- ✅ Cleaner `dir()` output (shows only public API)
- ✅ Cross-module reexports with `reexpose()`
- ✅ Supports aliasing: `@expose(name="alias")`
- ✅ Refactor-safe and declarative

---

## 🚀 Basic Usage

```python
from exposepy import expose

@expose
def foo():
    return 42

@expose(name="bar_alias")
def bar():
    return 123
```

### Result:

```python
import mymodule
print(mymodule.__all__)  # ['foo', 'bar_alias']
print(dir(mymodule))     # ['foo', 'bar_alias']
```

---

## 🔁 Cross-module Re-Export

```python
# module_a.py
from exposepy import expose

@expose
def internal_tool(): ...

# module_b.py
from module_a import internal_tool
from exposepy import reexpose

reexpose(internal_tool, name="public_tool")
```

Now `module_b.__all__ == ['public_tool']`.

---

## 📚 Reference

### `@expose`
```python
@expose
def symbol(): ...
```

Optionally rename:

```python
@expose(name="alias_name")
def symbol(): ...
```

---

### `reexpose`
```python
reexpose(symbol)
reexpose(symbol, name="alias")
```

Useful to re-export symbols across module boundaries cleanly.

---

## 🛠 Versioning

`exposepy` uses Git-based versioning.  
To see the current version:

```bash
pip show exposepy
```

---

## 🤝 Contributing

See the [GitHub repo](https://github.com/El3ssar/exposepy) and the `CONTRIBUTING.md`.

---

## 🔗 Links

- [GitHub](https://github.com/El3ssar/exposepy)
- [PyPI](https://pypi.org/project/exposepy/)
