# Python 3.13 Release Notes Digest

Handout digest for the Python 3.13 unit. Distilled from the official
[What's New in Python 3.13](https://docs.python.org/3/whatsnew/3.13.html) release notes.

## Highlights

- **Free-threaded CPython (PEP 703):** experimental support for running Python with the GIL disabled; use the `python3.13t` executable or build with `--disable-gil`; check with `sys._is_gil_enabled()`; pip 24.1+ is required to install packages with C extensions in the free-threaded build.
- **Experimental JIT compiler (PEP 744):** a basic JIT is included, disabled by default; build with `--enable-experimental-jit` and control it at runtime with `PYTHON_JIT=0`/`1`.
- **New interactive interpreter:** a new REPL by default (code from the PyPy project) with multiline editing, F1/F2/F3 commands, paste mode, and colored prompts and tracebacks; disable with `PYTHON_BASIC_REPL`, or control color with `PYTHON_COLORS`, `NO_COLOR`, `FORCE_COLOR`.
- **Improved error messages:** tracebacks are highlighted in color by default; clearer messages when a script shadows a standard library or third-party module; suggestions for likely misspelled keyword arguments.
- **Defined `locals()` semantics (PEP 667):** mutating the returned mapping now has defined behavior; `FrameType.f_locals` is a write-through proxy in optimized scopes; `exec()`/`eval()` run against independent snapshots.
- **Type parameters support defaults (PEP 696):** `typing.TypeVar`, `typing.ParamSpec`, and `typing.TypeVarTuple` now support default values.
- **New typing features (PEP 705, PEP 742):** `typing.ReadOnly` marks a `TypedDict` item as read-only for type checkers; `typing.TypeIs` provides more intuitive type narrowing as an alternative to `typing.TypeGuard`.
- **Platform support:** iOS is now an officially supported platform at tier 3 (PEP 730); `wasm32-wasi` is tier 2; `wasm32-emscripten` is no longer officially supported (PEP 738 brought Android to tier 3).
- **Security improvements:** `ssl.create_default_context()` now sets `ssl.VERIFY_X509_PARTIAL_CHAIN` and `ssl.VERIFY_X509_STRICT` as default flags.

## Notable deprecations

- **`dis.get_instructions()` `show_caches` argument is deprecated** and no longer has any effect; the new C-API route for monitoring events is the PEP 669 suite.
- **`importlib.resources.contents()` remains deprecated** in favor of the `Traversable` API; the release notes state there is now no plan to remove it.
- **`mimetypes.guess_type()` with filesystem paths is soft deprecated**; use `mimetypes.guess_file_type()` instead.
- **New argparse deprecation API:** `add_argument()` and `add_parser()` now accept a `deprecated` parameter for command-line options, positional arguments, and subcommands.
- **`warnings.deprecated()` decorator (PEP 702):** adds support for marking deprecations in the type system and at runtime.
- Removed in 3.13: the `2to3` tool and `lib2to3` module (deprecated in 3.11), the `tkinter.tix` module, `locale.resetlocale()`, and the `typing.io` and `typing.re` namespaces; chained `classmethod` descriptors are also removed.

## Source

What's New In Python 3.13 — https://docs.python.org/3/whatsnew/3.13.html
